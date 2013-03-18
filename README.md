HW-5
====
 #copyright (c) Erica Boulay
 #Pay Roll Program - Homework 5 DUE 03/20/2013



from Functions import *
#core definitions

yes_no_response = ["y","n"]
valid_responses = ["a","d", "m", "p"]
#create an empty dictionary to be used for payroll info
#every person will be a key-value pair in the same dictionary

payRoll = {}
newEmployee = []



def openFile():
#import the payroll data from the .txt file
    file = open('payroll.txt', 'r+')
    #convert the data from the .txt file into a list
    for line in file:
        newEmployee = line.rsplit(",")
        
        #return("Pay Roll Data:", "\n", line, end="")
        #newEmployee = (lastName), (firstName),(rate),(hours),(grossPay)
        #append to the payRoll dictionary
        
        payRoll[newEmployee[0]] =(newEmployee)
    file.close()

  
#Core menu function found here        
def printMenu():
    #prints out the menu of choices
    print("a - add a new employee", "\n", "d - delete an employee", "\n", "m - modify an employee", "\n", "p - print all employees")
    ch = str(input("Welcome to the Payroll System. What would you like to do? Select a choice. "))
    i = 0
    valid_responses = ["a","d", "m", "p"]
    responses(ch)

def responses(ch):
    while ch not in valid_responses:
        #print("not a valid response. Please choose: ", valid_responses)
        ch = str(input("Please enter a valid choice.  Choose: a, d, m, or p."))
        i += 1
    while ch in valid_responses:
        if ch == "a":
            addEmployee(payRoll)
        elif ch == "d":
            deleteEmployee(payRoll)
        elif ch == "m":
            modifyEmployee(payRoll)
        elif ch == "p":
            printEmployee(payRoll)
        else:
            ch = str(input("Not a valid choice.  Please choose: a, d, m, or p."))
        printMenu()               

def main():
    openFile()
    t='y'
    while t=='y':
        printMenu()
        t = str(input("Do you want to continue?"))     
    file = open(filename, "w")
    file.write(payRoll)
        # delete everything on the file and send everything in the employeeList at that moment out the file

main()
