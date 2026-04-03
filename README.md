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

## Data Model
Explanation of data model:

Our model is based on a hypothetical boutique fitness studio with locations throughout Georgia and Florida. The boutique operates on a membership subscription model that offers a basic or unlimited tier. The basic tier lets members attend only four classes per month, while the unlimited tier allows members to attend an unlimited amount of classes. The goal of this data model is to organize the boutique’s operational data to maximize efficiency while managing multiple locations, employees and trainers, monitoring class attendance, membership revenue, and ensuring member satisfaction.

Each studio location employs its own set of employees, trainers, and members, creating one-to-many relationships between entities Location and Employees, Trainers, and Members. This allows management to analyze the amount of employees and distribution of members across different regions in GA and FL. Members are able to purchase subscription plans, which are stored in the Memberships entity, and define their membership tier as basic or unlimited, setting their monthly class limits and price of their subscription.

Each class is taught by one trainer and takes place in one studio room, however trainers and studio rooms can take on many classes. Our boutique offers multiple types of classes to members such as Endurance, Strength, HIIT and Power Circuits, and Slow Flow yoga classes. Each studio room has a max capacity of 30 participants to ensure the safety and satisfaction of our members and trainers during class. Additionally, each studio room contains equipment such as treadmills, rowers, dumbbells, and yoga mats, creating a one-to-many relationship between our Studio_Rooms and Equipment entities and helping our boutique to effectively keep tabs on the equipment and their associated costs for each studio room.

Members can attend many classes and each class hosts many members, making our Attendance_Logs entity an associative table between Members and Classes. Attendance_Logs tracks the time that members check into class to determine if they check in on time or late. The entity also tracks the attendance status of the classes members commit to, enforcing boutique policies such penalties for members who “no-show” and tracking member participation trends. Members can also submit a review and a 1-5 star rating after attending a class, but only if their attended status verifies they attended.

Revenue is tracked through the Payments entity, which records transactions associated with each member’s subscription. Additionally, the Referrals entity captures potential new customers through our boutique referral program for existing members, allowing managers to measure the effectiveness of the program strategy.

<img width="1020" height="867" alt="image" src="https://github.com/user-attachments/assets/695598ca-3eee-45cc-abee-bcdef950898c" />

## Data Dictionary:
<img width="812" height="667" alt="image" src="https://github.com/user-attachments/assets/3c92fcb0-4e14-4dc7-8a7d-2904205c5d4a" />
<img width="896" height="567" alt="image" src="https://github.com/user-attachments/assets/95b5f273-9803-4859-b49d-5dd0bb1c9413" />
<img width="842" height="836" alt="image" src="https://github.com/user-attachments/assets/4e1d98e3-9bad-4c29-9eda-13ba30c3ce3f" />
<img width="818" height="343" alt="image" src="https://github.com/user-attachments/assets/c0697dc0-8279-46b0-adc9-be697ecb71af" />
<img width="815" height="632" alt="image" src="https://github.com/user-attachments/assets/315f4cc4-30d6-4611-bbed-006b8874478b" />
<img width="825" height="585" alt="image" src="https://github.com/user-attachments/assets/b188fd1f-9b6d-4947-8518-538f245da320" />
<img width="823" height="410" alt="image" src="https://github.com/user-attachments/assets/63182396-57f7-45ea-8cd0-2a8f0da68bd0" />
<img width="821" height="711" alt="image" src="https://github.com/user-attachments/assets/ab6e01f1-4bb8-42be-94ff-19e0fb0d5ed9" />



