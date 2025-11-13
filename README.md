# miniproject-pca

## OBJECTIVE:

File handling, lists/dictionaries, conditionals, loops

Add new student records

View all records

Search for a student

Calculate average marks

Store data permanently in a text file

## PROGRAM:

# Student Grade Management System

import os

FILE_NAME = "students.txt"

def add_student():
    name = input("Enter student name: ")
    roll = input("Enter roll number: ")
    marks = float(input("Enter marks: "))
    record = f"{roll},{name},{marks}\n"
    with open(FILE_NAME, "a") as file:
        file.write(record)
    print("Student added successfully!\n")

def view_students():
    if not os.path.exists(FILE_NAME):
        print("No records found.\n")
        return
    with open(FILE_NAME, "r") as file:
        print("Roll No\tName\tMarks")
        print("-"*25)
        for line in file:
            roll, name, marks = line.strip().split(",")
            print(f"{roll}\t{name}\t{marks}")
    print()

def search_student():
    roll = input("Enter roll number to search: ")
    found = False
    if os.path.exists(FILE_NAME):
        with open(FILE_NAME, "r") as file:
            for line in file:
                r, name, marks = line.strip().split(",")
                if r == roll:
                    print(f"Found -> Roll: {r}, Name: {name}, Marks: {marks}")
                    found = True
                    break
    if not found:
        print("Student not found.\n")

def average_marks():
    if not os.path.exists(FILE_NAME):
        print("No data available.\n")
        return
    total, count = 0, 0
    with open(FILE_NAME, "r") as file:
        for line in file:
            _, _, marks = line.strip().split(",")
            total += float(marks)
            count += 1
    if count > 0:
        print(f"Average Marks of Class: {total / count:.2f}\n")
    else:
        print("No students in record.\n")

def menu():
    while True:
        print("\n===== Student Grade Management =====")
        print("1. Add Student")
        print("2. View All Students")
        print("3. Search Student")
        print("4. Calculate Average Marks")
        print("5. Exit")
        choice = input("Enter your choice: ")
        
        if choice == '1':
            add_student()
        elif choice == '2':
            view_students()
        elif choice == '3':
            search_student()
        elif choice == '4':
            average_marks()
        elif choice == '5':
            print("Exiting Program...")
            break
        else:
            print("Invalid choice! Try again.\n")

menu()


## OUTPUT:
<img width="912" height="661" alt="image" src="https://github.com/user-attachments/assets/c36dcd85-3531-49a4-8589-d91b9e15f7b9" />




