#!/bin/bash

# Set the AWS profile environment variable
export AWS_PROFILE=default

# Function to check the number of arguments provided to the script
check_num_of_args() {
    if [ "$#" -ne 1 ]; then
        echo "Usage: $0 <environment>"
        exit 1
    fi
}

# Function to activate the appropriate environment based on user input
activate_infra_environment() {
    case "$ENVIRONMENT" in
        local)
            echo "Running script for Local Environment..."
            ;;
        testing)
            echo "Running script for Testing Environment..."
            ;;
        production)
            echo "Running script for Production Environment..."
            ;;
        *)
            echo "Invalid environment specified. Please use 'local', 'testing', or 'production'."
            exit 2
            ;;
    esac
}

# Function to check if AWS CLI is installed
check_aws_cli() {
    if ! command -v aws &> /dev/null; then
        echo "AWS CLI is not installed. Please install it before proceeding."
        exit 1
    fi
}

# Function to check if the AWS profile environment variable is set
check_aws_profile() {
    if [ -z "$AWS_PROFILE" ]; then
        echo "AWS profile environment variable is not set."
        exit 1
    else
        echo "Using AWS_PROFILE=$AWS_PROFILE"
    fi
}

# Function to create a security group with SSH and HTTP access
create_security_group() {
    local sg_name="datawise-security-group"
    local vpc_id=$(aws ec2 describe-vpcs --query 'Vpcs[0].VpcId' --output text)
    sg_id=$(aws ec2 create-security-group --group-name "$sg_name" --description "Security group for Datawise project" --vpc-id "$vpc_id" --query 'GroupId' --output text)
    
    if [ $? -ne 0 ]; then
        echo "Failed to create security group."
        exit 1
    fi
    
    # Allow SSH (port 22) and HTTP (port 80) access
    aws ec2 authorize-security-group-ingress --group-id "$sg_id" --protocol tcp --port 22 --cidr 0.0.0.0/0
    aws ec2 authorize-security-group-ingress --group-id "$sg_id" --protocol tcp --port 80 --cidr 0.0.0.0/0
    
    if [ $? -ne 0 ]; then
        echo "Failed to set security group rules."
        exit 1
    fi
    
    echo "Security group created with ID: $sg_id"
}

# Function to create a new key pair and save it locally
create_key_pair() {
    local key_name="test-keypair"
    
    if ! aws ec2 describe-key-pairs --key-names "$key_name" &> /dev/null; then
        aws ec2 create-key-pair --key-name "$key_name" --query 'KeyMaterial' --output text > "$key_name.pem"
        chmod 400 "$key_name.pem"
        echo "Key pair created and saved as $key_name.pem"
    else
        echo "Key pair '$key_name' already exists."
    fi
}

# Function to create EC2 instances with specified AMIs and configurations
create_ec2_instances() {
    local ami_ids=(
        "ami-08a0d1e16fc3f61ea"  # Amazon Linux
        "ami-04b70fa74e45c3917"  # Ubuntu
        "ami-002070d43b0a4f171"  # CentOS
    )
    local instance_type="t2.micro"
    local count=1
    local region="us-east-1"
    local key_name="test-keypair"
    local instance_names=("AmazonLinuxInstance" "UbuntuInstance" "CentOSInstance")

    for i in "${!ami_ids[@]}"; do
        local ami_id="${ami_ids[$i]}"
        local instance_name="${instance_names[$i]}"
        
        echo "Creating EC2 instance with AMI $ami_id and Name tag $instance_name..."
        
        instance_id=$(aws ec2 run-instances \
            --image-id "$ami_id" \
            --instance-type "$instance_type" \
            --count "$count" \
            --region "$region" \
            --key-name "$key_name" \
            --security-group-ids "$sg_id" \
            --tag-specifications "ResourceType=instance,Tags=[{Key=Name,Value=$instance_name}]" \
            --query 'Instances[0].InstanceId' \
            --output text)
        
        if [ $? -eq 0 ]; then
            echo "EC2 instance created successfully with AMI $ami_id. Instance ID: $instance_id"
        else
            echo "Failed to create EC2 instance with AMI $ami_id."
            exit 1
        fi
    done
}

# Function to create S3 buckets for various departments
create_s3_buckets() {
    local company="datawise"
    local departments=("marketing" "sales" "hr" "operations" "media")

    for department in "${departments[@]}"; do
        local bucket_name="${company}-${department}-data-bucket"
        
        # Check if the bucket already exists
        if ! aws s3api head-bucket --bucket "$bucket_name" &> /dev/null; then
            echo "Creating S3 bucket: $bucket_name"
            
            if aws s3api create-bucket --bucket "$bucket_name" --region us-east-1; then
                echo "S3 bucket '$bucket_name' created successfully."
            else
                echo "Failed to create S3 bucket '$bucket_name'."
                return 1
            fi
        else
            echo "S3 bucket '$bucket_name' already exists."
        fi
    done
}

# Function to upload a script to all EC2 instances
upload_script_to_instances() {
    local instance_names=("AmazonLinuxInstance" "UbuntuInstance" "CentOSInstance")

    for instance_name in "${instance_names[@]}"; do
        local instance_id=$(aws ec2 describe-tags --filters "Name=tag:Name,Values=$instance_name" --query 'Tags[0].ResourceId' --output text)
        local public_ip=$(aws ec2 describe-instances --instance-ids "$instance_id" --query 'Reservations[*].Instances[*].PublicIpAddress' --output text)
        
        if [ -n "$public_ip" ]; then
            echo "Uploading script to instance $instance_id ($instance_name) at $public_ip..."
            
            scp -i "test-keypair.pem" -o StrictHostKeyChecking=no script.sh ec2-user@"$public_ip":/home/ec2-user/
            
            if [ $? -eq 0 ]; then
                echo "Script uploaded to instance $instance_id ($instance_name)."
            else
                echo "Failed to upload script to instance $instance_id ($instance_name)."
                return 1
            fi
        else
            echo "No public IP found for instance $instance_id ($instance_name)."
        fi
    done
}

# Function to execute a script on all EC2 instances
execute_script_on_instances() {
    local instance_names=("AmazonLinuxInstance" "UbuntuInstance" "CentOSInstance")

    for instance_name in "${instance_names[@]}"; do
        local instance_id=$(aws ec2 describe-tags --filters "Name=tag:Name,Values=$instance_name" --query 'Tags[0].ResourceId' --output text)
        local public_ip=$(aws ec2 describe-instances --instance-ids "$instance_id" --query 'Reservations[*].Instances[*].PublicIpAddress' --output text)
        
        echo "Executing script on instance $instance_id ($instance_name) at $public_ip..."
        
        ssh -i "test-keypair.pem" -o StrictHostKeyChecking=no ec2-user@"$public_ip" 'bash /home/ec2-user/script.sh'
        
        if [ $? -eq 0 ]; then
            echo "Script executed on instance $instance_id ($instance_name)."
        else
            echo "Failed to execute script on instance $instance_id ($instance_name)."
            return 1
        fi
    done
}

# Function to install and start Apache on instances based on OS type
install_and_start_apache() {
    local os=$1

    case "$os" in
        "Amazon Linux" | "CentOS")
            sudo yum install -y httpd
            sudo systemctl start httpd
            sudo systemctl enable httpd
            ;;
        "Ubuntu")
            sudo apt-get update
            sudo apt-get install -y apache2
            sudo systemctl start apache2
            sudo systemctl enable apache2
            ;;
        *)
            echo "Unsupported OS: $os"
            exit 1
            ;;
    esac

    echo "Apache installed and started on $os."
}

# Function to deploy a sample web application on instances based on OS type
deploy_sample_web_app() {
    local os=$1
    local content="<html><body><h1>Hello from $os</h1></body></html>"

    case "$os" in
        "Amazon Linux" | "CentOS" | "Ubuntu")
            echo "$content" | sudo tee /var/www/html/index.html
            ;;
        *)
            echo "Unsupported OS: $os"
            exit 1
            ;;
    esac

    echo "Sample web application deployed on $os."
}

# Function to verify web application accessibility
verify_web_app_access() {
    local instance_names=("AmazonLinuxInstance" "UbuntuInstance" "CentOSInstance")

    for instance_name in "${instance_names[@]}"; do
        local instance_id=$(aws ec2 describe-tags --filters "Name=tag:Name,Values=$instance_name" --query 'Tags[0].ResourceId' --output text)
        local public_ip=$(aws ec2 describe-instances --instance-ids "$instance_id" --query 'Reservations[*].Instances[*].PublicIpAddress' --output text)
        
        response=$(curl -s -o /dev/null -w "%{http_code}" "http://$public_ip")
        
        if [ "$response" -eq 200 ]; then
            echo "Web application is accessible on instance $instance_id ($instance_name)."
        else
            echo "Web application is not accessible on instance $instance_id ($instance_name)."
            exit 1
        fi
    done
}

# Array of IAM user names
iam_user_names=("user1" "user2" "user3" "user4" "user5")

# Function to create IAM users
create_iam_users() {
    for username in "${iam_user_names[@]}"; do
        echo "Creating IAM user: $username..."
        
        if ! aws iam get-user --user-name "$username" &> /dev/null; then
            aws iam create-user --user-name "$username"
            
            if [ $? -eq 0 ]; then
                echo "IAM user $username created successfully."
            else
                echo "Failed to create IAM user $username."
                return 1
            fi
        else
            echo "IAM user $username already exists."
        fi
    done
}

# Function to create IAM group
create_iam_group() {
    local group_name="admin"
    echo "Creating IAM group: $group_name..."
    
    if ! aws iam get-group --group-name "$group_name" &> /dev/null; then
        aws iam create-group --group-name "$group_name"
        
        if [ $? -eq 0 ]; then
            echo "IAM group $group_name created successfully."
        else
            echo "Failed to create IAM group $group_name."
            return 1
        fi
    else
        echo "IAM group $group_name already exists."
    fi
}

# Function to attach administrative policy to group
attach_admin_policy_to_group() {
    local group_name="admin"
    local policy_arn="arn:aws:iam::aws:policy/AdministratorAccess"
    echo "Attaching AdministratorAccess policy to group $group_name..."
    
    aws iam attach-group-policy --group-name "$group_name" --policy-arn "$policy_arn"
    
    if [ $? -eq 0 ]; then
        echo "AdministratorAccess policy attached to group $group_name."
    else
        echo "Failed to attach AdministratorAccess policy to group $group_name."
        return 1
    fi
}

# Function to assign users to group
assign_users_to_group() {
    for username in "${iam_user_names[@]}"; do
        echo "Adding user $username to group admin..."
        aws iam add-user-to-group --user-name "$username" --group-name admin
        
        if [ $? -eq 0 ]; then
            echo "User $username added to group admin."
        else
            echo "Failed to add user $username to group admin."
            exit 1
        fi
    done
}

# Main script execution starts here
# Set the environment variable
ENVIRONMENT=$1

# Check the number of arguments
check_num_of_args "$@"

# Activate the appropriate environment
activate_infra_environment

# Check if AWS CLI is installed
check_aws_cli

# Check if AWS profile is set
check_aws_profile

# Create security group
create_security_group

# Create key pair
create_key_pair

# Create EC2 instances
create_ec2_instances

# Create S3 buckets
create_s3_buckets

# Upload script to instances
upload_script_to_instances

# Execute script on instances
execute_script_on_instances

# Install and start Apache
install_and_start_apache "Amazon Linux"
install_and_start_apache "Ubuntu"
install_and_start_apache "CentOS"

# Deploy sample web application
deploy_sample_web_app "Amazon Linux"
deploy_sample_web_app "Ubuntu"
deploy_sample_web_app "CentOS"

# Verify web application accessibility
verify_web_app_access

# Manage IAM users
create_iam_users
create_iam_group
attach_admin_policy_to_group
assign_users_to_group
