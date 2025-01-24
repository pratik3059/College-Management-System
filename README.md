# College-Management-System

class Student(): 
    def __init__(self,studentid,name,age,percentage = 0):
        self.studentid = studentid
        self.name = name
        self.age = age
        self.percentage = percentage

    def display(self):
        print("Student ID :",self.studentid)
        print("Student Name :",self.name)
        print("Age :",self.age)
        print("Percentage :",self.percentage)

    def calculatMarks(self):
        if (self.percentage>=75 and self.percentage<100):
            print("First Class Distinction")
        elif(self.percentage>=60 and self.percentage<75):
            print("First Class")
        elif(self.percentage >=50 and self.percentage<60):
            print("Second Class")
        elif (self.percentage >=40 and self.percentage<50):
            print("Pass")
        else:
            print("Failed")

    def __str__(self):
        return str(self.studentid) + self.name + str(self.age) + str(self.percentage)

class engStudent(Student):
    def __init__(self,branch,internalmarks,studentid,name,age,percentage):
        super().__init__(studentid,name,age,percentage)
        self.branch = branch
        self.internalmarks = internalmarks

    def display(self):
        super().display()
        print("Branch :",self.branch)

    def calculatMarks(self):
        print(f"Debug: Percentage = {self.percentage},Internal Marks = {self.internalmarks}")
        if (self.percentage>=75 and self.internalmarks>40):
            print("First Class Distinction")
        elif(self.percentage>=60 and self.internalmarks>30):
            print("First Class")
        elif(self.percentage >=50 and self.internalmarks>20):
            print("Second Class")
        elif (self.percentage >=40 and self.internalmarks>10):
            print("Pass")
        else:
            print("Failed")

    def __str__(self):
        return str(self.internalmarks)+self.branch

class MedicalStudent(Student):
    def __init__(self, specialization, marksofinternship, studentid, name, age, percentage):
        super().__init__(studentid, name, age, percentage)
        self.specialization = specialization
        self.marksofinternship = marksofinternship

    def display(self):
        super().display()
        print("Specialization :", self.specialization)
        print("Marks Of Internship :", self.marksofinternship)

    def calculatMarks(self):
        print(f"Debug: Percentage = {self.percentage}, Marks of Internship = {self.marksofinternship}")
        if self.percentage >= 75 and self.marksofinternship > 40:
            print("First Class Distinction")
        elif self.percentage >= 60 and self.marksofinternship > 30:
            print("First Class")
        elif self.percentage >= 50 and self.marksofinternship > 20:
            print("Second Class")
        elif self.percentage >= 40 and self.marksofinternship > 10:
            print("Pass")
        else:
            print("Failed")

    def __str__(self):
        return self.specialization+str(self.marksofinternship)
class college:
    def __init__(self):
        self.no_student = []

    def addStudent(self):
        print("Select__1__for geting student details")
        print("Select__2__for geting  Engineer student details")
        print("Select__3__for geting  Medical student details")
        ch = int(input("Enter Your Choice :"))
        if(ch == 1):
            studentid = int(input("Enter Student ID :"))
            name = input("Enter Name :")
            age = int(input("Enter Age :"))
            percentage =int(input("Enter Percentage"))
            s =Student(studentid,name,age,percentage)
            self.no_student.append(s)
        elif(ch == 2):
            branch = input("Enter Branch :")
            internalmarks = int(input("Enter InternalMarks :"))
            studentid = int(input("Enter Student ID :"))
            name = input("Enter Name :")
            age = int(input("Enter Age :"))
            percentage = int(input("Enter Percentage"))
            s =  engStudent(branch, internalmarks, studentid, name, age, percentage)
            self.no_student.append(s)
        elif(ch == 3):
            specialization = input("Enter Specialization ")
            marksofinternship = int(input("Enter Marks :"))
            studentid = int(input("Enter Student ID :"))
            name = input("Enter Name :")
            age = int(input("Enter Age :"))
            percentage = int(input("Enter Percentage"))
            s = MedicalStudent(specialization, marksofinternship, studentid, name, age, percentage)
            self.no_student.append(s)
        else:
            print("Invalid Choice Number Please Enter Correct")

    def getStudent(self,id=0):
        id = int(input("Enter id"))
        for stud in self.no_student:
            if student.id == id:
                return stud
        return "Not Found"
    def removeStudent(self):
        id = int(input("Enter ID For Remove"))
        for student in self.no_student:
            if(student.id == id):
                self.no_student.remove(student)
                break
        else:
            print("Not Found")


c = college()
while (True):
    print("1__Select 1 for getting student information")
    print("2__Select 2 for removing student information")
    choice = int(input("Enter Choice"))
    if choice == 1:
        c.addStudent()
    elif choice == 2:
        student_id = int(input("Enter Student ID to Display: "))
        student = c.getStudent(student_id)
        if student:
            student.display()
        else:
            print("Student Not Found.")
    elif choice == 3:
        c.removeStudent()
    elif choice == 4:
        print("Exiting Program")
        break
    else:
        print("Invalid Choice!")
