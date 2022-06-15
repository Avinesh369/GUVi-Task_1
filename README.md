# GUVi-Task_1
# Python program to validate an Email

import re
 
# Make a regular expression
# for validating an Email
regex = r'\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b'
 
# Define a function for
# for validating an Email
 
def check(email):
 
    # pass the regular expression
    # and the string into the fullmatch() method
    if(re.fullmatch(regex, email)):
        print("Valid Email")
        return True
 
    else:
        print("Invalid Email")
        return False
        
# Password validation in Python
# using naive method
  
# Function to validate the password
def password_check(passwd):
      
    SpecialSym =['$', '@', '#', '%']
    val = True
      
    if len(passwd) < 5:
        print('length should be at least 5')
        val = False
          
    if len(passwd) > 16:
        print('length should be not be greater than 16')
        val = False
          
    if not any(char.isdigit() for char in passwd):
        print('Password should have at least one digit')
        val = False
          
    if not any(char.isupper() for char in passwd):
        print('Password should have at least one uppercase character')
        val = False
          
    if not any(char.islower() for char in passwd):
        print('Password should have at least one lowercase character')
        val = False
          
    if not any(char in SpecialSym for char in passwd):
        print('Password should have at least one of the symbols $@#')
        val = False
       
    if (val):
        print("Password is valid")
        return True
    else:
        print("Invalid Password !!")
        return False  


# writing new content to the file
fp = open("Registration.txt", 'w')

email_ = input("Enter the email:")
passwrd = input("Enter the password:")

if (check(email_) and password_check(passwrd)):
  fp.write(email_)
  fp.write(",  " + passwrd)

print('User Stored')
fp.close()

# Open the file for reading the new contents
fp = open("Registration.txt", 'r')
print(fp.read())
fp.close()
