from random import *
import math

##################################################################################################
def main():
    print("Welcome")
    initializer = True
    while (initializer == True):
        choice = menuScreen()
        if (choice == "enter"):
            #overwrite the previous list
            studentNames = enterStudentNames()
        elif (choice == "create"):
            #read and copy names to an array
            studentsList = readNamesFromTextFile()
            #find class size by checking length of the studentsList array
            classSize = findClassSize(studentsList)
            #just randomize the names n times, where n is size of class
            studentsList = randomizeNames(studentsList,classSize)
            #find out how big the user wants the groups to be
            groupSize = findGroupSize()
            #generate combinations without repeat with a simple .append and pop
            combinations = generateCombinations(classSize,groupSize,studentsList)
            #ask user how many groups they want and touch up the groups to the specifications
            #still in progress
            #combinations = askNumberOfGroups(combinations,groupSize)
            #print the combinations
            #needs to be modefied if top function gets implimented
            initializer = printStudentGroups(combinations,groupSize,initializer)
        elif (choice == "delete"):
            #read and copy names to an array
            studentsList = readNamesFromTextFile()
            #print all the names for display
            printNames(studentsList)
            #delete the name from the array
            studentsList = deleteNames(studentsList)
            #overwrite the text file
            overwriteTextFile(studentsList)
        elif (choice == "print"):
            #read and copy names to an array
            studentsList = readNamesFromTextFile()
            #simply print the names from list
            printNames(studentsList)
        elif (choice == "add"):
            #read and copy names to an array
            studentsList = readNamesFromTextFile()
            #append the name to the list of students
            studentsList = addNames(studentsList)
            #overwrite the text file
            overwriteTextFile(studentsList)
        elif (choice == "help"):
            #display help
            initilizer = displayHelp(initializer)
        elif (choice == "quit"):
            #stop the loop
            initializer = False      
##################################################################################################
def menuScreen():
    print("Please select one of the folowing:\n")
    print("Enter:  Enter student names(s)        Add:    Add a student name(s)")
    print("Print:  Print name(s) from list       Delete: Delete student name(s)")
    print("Create: Create random groups          Help: Display help screen")
    print("Quit:   Quit \n")
    
    choice = input("Choice: ")
    choice = choice.lower()
    
    while (choice != 'enter' and choice != 'create' and choice != 'delete' and choice != 'print'
           and choice != 'quit' and choice != 'add'and choice != 'help'):
        print("Invalid Coice\n")
        print("Enter:  Enter student names(s)        Add:    Add a student name(s)")
        print("Print:  Print name(s) from list       Delete: Delete student name(s)")
        print("Create: Create random groups          Help: Display help screen")
        print("Quit:   Quit\n")
        
        choice = input("Choice: ")
        choice.lower()
    return choice
##################################################################################################
def displayHelp(initilizer):
    print('Type full words')
    print("Capitolization does not matter\n")
    
    pause = input('Press any key to continue or type "Quit" to quit ')
    print("")
    
    if (pause.lower() == "Quit"):
        initializer = False
##################################################################################################
def enterStudentNames():
    #automatically create a new text file named studentNames.txt in the folder
    #where this file is located as WRITE ONLY
    file = open("studentNames.txt","w")

    #create empty list
    students = []

    print("Enter 0 to quit\n")
    #variable to store input in
    name = input("Enter Name: ")
    
    while (name != '0'):
        #append the list with an added name
        students.append(name)
        name = input("Enter Name: ")

    length = len(students)
    index = 0
    
    while (index < length):
        studentName = students[index]
        file.write(studentName+' \n')
        index += 1

    #close the opened file
    file.close()

    return students
##################################################################################################
def readNamesFromTextFile():
    studentsList = []
    index = 0

    with open ('studentNames.txt','r') as file:
        for line in file:
            line = line.strip()
            studentsList.append(line)

    #close the opened file
    file.close()

    return studentsList
##################################################################################################
def printNames(studentsList):
    size = len(studentsList)
    
    print("There are: ", size, "student(s) in your class")
    studentsList.sort()
    
    for i in range (0,size):
        print(studentsList[i])
    
    print("")
##################################################################################################
def overwriteTextFile(studentsList):
    file = open("studentNames.txt","w")

    size = len(studentsList)
    
    for index in range (0,size):
        studentName = studentsList[index]
        file.write(studentName+' \n')

    file.close()
##################################################################################################
def addNames(studentsList):
    print ("Enter 0 to quit\n")
    name = input("Add name: ")
    
    while (name!='0'):
        studentsList.append(name)
        
        name = input("Add name: ")
        
    return studentsList
##################################################################################################
def deleteNames(studentsList):
    print ("Enter 0 to quit")
    if (len(studentsList) == 0):
        print('Oops, there are no names in your list...')
        print('Going back to main menu')
        name = "0"
    else:
        name = input("Delete name: ")
    
    while (name!='0'):
        if name in studentsList:
            studentsList.remove(name)

            print(name,"Deleted\n")
            name = input("Delete name: ")
        elif (len(studentsList) == 0):
            print('Oops, there are no names in your list...')
            print('Going back to main menu')
            name = "0"
        else:
            print("Name not found!")
            name = input("Delete name: ")
        
    return studentsList
##################################################################################################
def findClassSize(studentsList):
    classSize = len(studentsList)
    
    return classSize
##################################################################################################
def findGroupSize():
    groupSize = eval(input("How big are the groups? : "))

    return groupSize
##################################################################################################
def randomizeNames(studentsList,classSize):
    i = classSize-1
    while i > 1:
        i = i - 1
        j = randrange(i)  # 0 <= j <= i-1
        studentsList[j], studentsList[i] = studentsList[i], studentsList[j]
    return studentsList
##################################################################################################
def generateCombinations(classSize,groupSize,studentsList):
    i = classSize-1
    #rearange the names baised on how big the class is
    for k in range (0,classSize):
        while i > 1:
            i = i - 1
            j = randrange(i)  # 0 <= j <= i-1
            studentsList[j], studentsList[i] = studentsList[i], studentsList[j]

    #counter for comparing to group size
    counter = 0
    #index of individual groups
    groupIndex = 0
    #new list of lists to store groups in
    combinations = []
    combinations.append([])
    
    #keep checking the size of the students list because first name is always popped
    while (len(studentsList) != 0):
        student = studentsList[0]
        
        individualGroup = combinations[groupIndex]
        individualGroup.append(student)
        counter += 1
        #name is now in a new variable so pop it
        studentsList.pop(0)
        if counter == groupSize and len(studentsList) != 0:
            counter = 0
            combinations.append([])
            groupIndex += 1
            
    return combinations
##################################################################################################
def askNumberOfGroups(combinations,groupSize):
    print("There are",len(combinations),"possible")
    groupsWanted = eval(input("How many groups do you want?: "))
    repeat = True
    while (repeat == True):
        
        if (groupsWanted < len(combinations)):
            print("Do you want me to try rearanging groups?")
            answer = input('The groups will be uneven: ')
            if (answer.lower() == 'yes'):
                combinations = rearangeGroups(combinations,groupsWanted,groupSize)
            else:
                repeat = False
        elif (groupsWanted < len(combinations)):
            print("Do you want me to try rearanging groups?")
            answer = input('The groups will be uneven: ')
            if (answer.lower() == 'yes'):
                combinations = rearangeGroups(combinations,groupsWanted,groupSize)
            else:
                repeat = False
        else:
            repeat = False
            
    return combinations
##################################################################################################
def rearangeGroups(combinations,groupsWanted,groupSize):
    numberOfGroups = len(combinations)
    
    while (len(combinations)<groupsWanted):
        combinations.append([])
        for i in range (0,groupSize):
            print("")
            
##################################################################################################
def printStudentGroups(combinations,groupSize,initializer):
    print(combinations)
    numberOfGroups = len(combinations)
    
    for x in range (0,numberOfGroups):
        group = combinations[x]
        print ("\nGroup: #",(x+1))
        groupSize = len(group)
        
        for y in range (0,groupSize):
            print(group[y])
            
    pause = input('Press any key to continue or type "Quit" to quit ')
    print("")
    
    if (pause.lower() == "Quit"):
        initializer = False
    return initializer
##################################################################################################
main()
