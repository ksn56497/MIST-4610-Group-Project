# Team 6 Mist 4610 Group Project 1

## Team Name: 
Group 6 

## Team Members:

1. Jesse Williams: [@jesnw](https://github.com/jeswn/group_project)
2. Tania Saputera: 
3. Kate Nelms: [@ksn56497](https://github.com/ksn56497/MIST-4610-Group-Project)
4. John Omolon: 
5. Johan: 

## Scenario Description :
Our data model follows an upscale boutique fitness studio with locations throughout Georgia and Florida. This fitness studio employs a subscription model with two tiers: a basic tier, with four classes a month, and an unlimited tier. This data model is designed to model accurate entity relationships and organize data. This is to manage multiple locations, track employees, monitor class attendance, optimize membership revenue, and manage class ratings. Therefore, providing business insights to optimize the fitness studio’s administration.  

Table: Employees
Column Name
Description
Data Type
Size
Format
Key
employeeID
PK, unique sequential number identifying each employee
INT
4


PK
employeeFName
First name of Employee
VARCHAR
45




employeeLName
Last name of Employee
VARCHAR
45




employeeAddress
Street address of Employee
VARCHAR
45




employeeCity
City where employee resides
VARCHAR
45




employeeState
State where employee resides (abbreviation)
VARCHAR
2
AA


employeePhoneNumber
Employee primary phone number
VARCHAR
14
(999)999-9999


locationID
Identifies the location where the employee works
INT
3
3
FK - Locations

