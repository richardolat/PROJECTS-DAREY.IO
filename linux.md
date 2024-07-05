[ec2-user@ip-172-31-24-229 ~]$ cat aws_cloud_manager.sh
#!/bin/bash
# # Define the IAM user names array
# iam_users=("user1" "user2" "user3" "user4" "user5")
# # Function to create IAM users
# create_iam_users() { for user in "${iam_users[@]}" do aws iam create-user --user-name "$user" done }
#  # Function to create IAM group
#  create_iam_group() { aws iam create-group --group-name "admin" }
#  # Function to attach administrative policy to group
#  attach_admin_policy() { aws iam attach-group-policy --group-name "admin" --policy-arn "arn:aws:iam::aws:policy/AdministratorAccess" }
#  # Function to assign users to group
#  assign_users_to_group() { for user in "${iam_users[@]}" do aws iam add-user-to-group --group-name "admin" --user-name "$user" done }
#  # Main script execution
#  create_iam_users
#  create_iam_group
#  attach_admin_policy
#  assign_users_to_group
