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
<img width="822" height="675" alt="image" src="https://github.com/user-attachments/assets/0a106d4d-3ba8-4908-8750-10a37b1f16a3" />
<img width="821" height="282" alt="image" src="https://github.com/user-attachments/assets/806cde52-eee6-4ec5-a3b7-7b9171d11b15" />
<img width="816" height="710" alt="image" src="https://github.com/user-attachments/assets/334295bc-caa4-48c7-beb8-072f835cb88d" />
<img width="816" height="332" alt="image" src="https://github.com/user-attachments/assets/21e083fb-cb21-4084-83df-9c737b7f1a62" />
<img width="812" height="321" alt="image" src="https://github.com/user-attachments/assets/f458eb8c-5862-4707-b88e-ed5cf5cefd21" />
<img width="817" height="640" alt="image" src="https://github.com/user-attachments/assets/24b17eb0-d58d-4ad8-abea-791927984094" />
<img width="817" height="576" alt="image" src="https://github.com/user-attachments/assets/7588816b-25c4-478c-a20e-0890fc402f7f" />
<img width="812" height="406" alt="image" src="https://github.com/user-attachments/assets/962101a8-7c7a-45c7-b990-fc34a6e62c99" />
<img width="811" height="687" alt="image" src="https://github.com/user-attachments/assets/d895b71d-3872-4ed5-9274-a08d07081ae2" />










