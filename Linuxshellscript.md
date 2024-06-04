## LINUX SHELL SCRIPTING : This project focuses on the use of Loops, handling user's input, and aplying condictional logic in bash scripting



1. #### I created and opened a file named analytical.sh by running the command "sudo vim analytical.sh"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/9965aa14-b156-42c2-8d5e-e760bd96bc2d)









2. #### I entered the shebang by typing "#!/bin/bash
   ![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/3af06cc0-8596-4e11-ab79-4f7905405157)







3. #### Then I ran the comment  #Prompt user to enter a number for the multiplication table. That is, echo -n "Enter a number for the multiplication table: "read -r number
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/850357d0-9151-4f35-9851-394d23162be4)









4. #### I defined the list of numbers to be generated. #Define the list of numbers numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10] 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/ad6d0deb-b962-4b33-b88a-5820736775b9)








5. #### Using loop, the list will, be iterated over for num in numbers. The command script goes thus;  # Use a for loop to iterate over the list for num in numbers; do  # Perform some operation on each number echo "Multiplying $num by 2 gives $num * 2" done
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/db5c8a14-7fda-49b5-959d-b12942dfa99b)









6. #### Then I asked to choose between full and partial tables. The script reads "# Ask user if they want a full table or partial table,  echo -n "Do you want a full table or a partial table? (f/p): ", read -r response
 ![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/30197702-1af8-44f4-9ff3-915719e6fcd2)







7. #### Using the if, I wrote;  #If user wants a partial table, prompt for start and end numbers if [ "$response" = "p" ]; then echo -n "Enter the start number of the range: " read -r start echo -n "Enter the end number of the range: " read -r end
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/3b6e3c6c-e10b-4116-89cc-56347f1f6c4f)









8.#### Then, the numbers are validated. # Validate the range input if [ "$start" -lt "1" ]; then echo "Invalid start number. Please enter a number greater than 0." start=1 fi 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/163f18df-745e-49d6-88c3-6eae4d448fc9)











9.#### If the end number is less than the starting number, then it will respond "invalid end number. Scripted as "if [ "$end" -lt "$start" ]; then echo "Invalid end number. Please enter a number greater than the start number." end=$start fi
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/3db45353-5dff-4dd0-ac10-81f202d16d19)












10.#### If user enters a number that's out of range, the script has this; #Handle invalid or out-of-bound entries if [ "$start" -gt "$number" ]; then echo "Start number is out of bounds. Please enter a number less than or equal to $number." start=1 fi
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/1c79efdf-9953-44cb-9612-13a62f19341b)








11.#### Then, if the end number is greater than the number in range, then the user gets "end number out of bound. scripted as; if [ "$end" -gt "$number" ]; then echo "End number is out of bounds. Please enter a number less than or equal to $number." end=$number fi
 ![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/0ae8fe94-0c9a-4ff6-bab1-99acfdaa8000)













12.####   # Generate and display multiplication table for the specified range  for i in $(seq "$start" "$end"); do echo -n "$i x $number = " result=$(($i * $number)) echo -n "$result " done } else {  # Generate and display full multiplication table for i in $(seq "1" "$number"); do echo -n "$i x $number = "
result=$(($i * $number)) echo -n "$result " done }
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/bccd2073-c28f-4281-b90b-4f580011072b)



































































































