```python
import pickle
import os

#Funtion to add employee details
def add_emp():
    file = open("employee.dat","ab")
    empID = input("Enter Employee ID")
    empName = input("Enter Employee Name")
    empAdd = input("Enter Employee Address")
    empPay = input("Enter Employee Salary")

    pickle.dump(empID,file)
    pickle.dump(empName,file)
    pickle.dump(empAdd,file)
    pickle.dump(empPay,file)
    file.close()
    
    print("Details for employee id: ",empID," added succesfully!")
    input("Press any key to continue")

#Function to view employee data
def view_all():
    file = open("employee.dat","rb")
    try:
        while(True):
            count = 0
            data = pickle.load(file)
            print(data, end=" ")
            count += 1
            if count%4 == 0:
                print("\n\n")
    except EOFError:
        print("** End of File **")
        input("Press any key to continue")

    file.close()

#Function to view employee details by ID
def view_id():
    file = open("employee.dat","rb")
    eID = input("Enter Employee ID:")
    userFound = 0
    try:
        while(True):
            data = pickle.load(file)
            if data == eID:
                print("\n\t Employee ID: ", data)
                print("\t Employee Name: ", pickle.load(file))
                print("\t Employee Address: ", pickle.load(file))
                print("\t Employee Salary: ", pickle.load(file))
                userFound += 1
    except EOFError:
        if userFound == 0:
            print("Employee not found")
        else:
            print("")
        input("Press any key to continue: ")
        
    
    file.close()
    
#Function to delete employee details
def del_emp():
    file = open("employee.dat","rb")
    temp = open("temp.dat","ab")
    userFound = 0
    empid = input("Enter Employee ID to be deleted")
    try:
        while(True):
            data = pickle.load(file)
            if data == empid:
                pickle.load(file)
                pickle.load(file)
                pickle.load(file)
                userFound = 1
            else:
                pickle.dump(data,temp)
    except EOFError:
        if userFound == 0:
            print("Employee not found")
        else:
            print("Employee deleted succesfully")
        input("Press any key to continue: ")
    file.close()
    temp.close()
    os.remove("employee.dat")
    os.rename("temp.dat","employee.dat")            

while (True):
    print('''\n\t**** EMPLOYEE MANAGEMENT SYSTEM ****
    
    1. Add Employee
    2. View All Employee
    3. View Employee via ID
    4. Delete Employee
    
    5. Exit
    ''')
    print(" ")
    n = int(input("Enter Selection"))
    if n == 5:
        break
    elif n == 1:
        add_emp()
    elif n == 2:
        view_all()
    elif n == 3:
        view_id()
    elif n == 4:
        del_emp()
    else:
        ...
    
```

    
    	**** EMPLOYEE MANAGEMENT SYSTEM ****
        
        1. Add Employee
        2. View All Employee
        3. Add Employee via ID
        4. Delete Employee
        
        5. Exit
        
     


    Enter Selection 2


    ** End of File **


    Press any key to continue 


    
    	**** EMPLOYEE MANAGEMENT SYSTEM ****
        
        1. Add Employee
        2. View All Employee
        3. Add Employee via ID
        4. Delete Employee
        
        5. Exit
        
     


    Enter Selection 1
    Enter Employee ID 101
    Enter Employee Name Mili
    Enter Employee Address Noida
    Enter Employee Salary 100000


    Details for employee id:  101  added succesfully!


    Press any key to continue 


    
    	**** EMPLOYEE MANAGEMENT SYSTEM ****
        
        1. Add Employee
        2. View All Employee
        3. Add Employee via ID
        4. Delete Employee
        
        5. Exit
        
     


    Enter Selection 1
    Enter Employee ID 102
    Enter Employee Name Ayushman
    Enter Employee Address Noida
    Enter Employee Salary 26800


    Details for employee id:  102  added succesfully!


    Press any key to continue 


    
    	**** EMPLOYEE MANAGEMENT SYSTEM ****
        
        1. Add Employee
        2. View All Employee
        3. Add Employee via ID
        4. Delete Employee
        
        5. Exit
        
     


    Enter Selection 2


    101 Mili Noida 100000 102 Ayushman Noida 26800 ** End of File **


    Press any key to continue 


    
    	**** EMPLOYEE MANAGEMENT SYSTEM ****
        
        1. Add Employee
        2. View All Employee
        3. Add Employee via ID
        4. Delete Employee
        
        5. Exit
        
     


    Enter Selection 3
    Enter Employee ID: 101


    
    	 Employee ID:  101
    	 Employee Name:  Mili
    	 Employee Address:  Noida
    	 Employee Salary:  100000
    


    Press any key to continue:  


    
    	**** EMPLOYEE MANAGEMENT SYSTEM ****
        
        1. Add Employee
        2. View All Employee
        3. Add Employee via ID
        4. Delete Employee
        
        5. Exit
        
     


    Enter Selection 5



```python

```
