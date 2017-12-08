# Tiger Check-Out

***A database based Check-Out platform for University of Missouri.***

## Video URL
https://www.youtube.com/watch?v=xSwDqnKpt9g

## Members List
 - Yiqing Wang (yw283)
 - ChunBin Lin (clpk8)
 - Miaoqing Chen (mcc66) -- Add-On
 - Zhengyu Li (zlr25) -- Add-On

## Project Description
This project is implemented as a check-out system for University of Missouri. 
Firstly, the users are required to enroll in our system. 
For this part, our system has been designed to read and store user information in User.db by inputing from keyboard and scanning the magnetic strip student cards. 
After the users login our system, he/she can see a list of items which are available to borrow. If the user borrows an item in this step, the item will be moved from List of Available Item to Borrowed Item.
The user can also return the borrowed items in this step. 
Once the user wants to return the borrowed item, our system will use the built-in camera of laptop to scan the QR code on the back of each item.
On the other hand, since each item has the unique length of lending period, an automatic reminder email will be sent to the borrowers before they exceed their lending periods.
Our system also has an admin account which has the privilege to add and delete items from Item.db. The admin can also see the detail infomation of each borrowed item.

## Schema for the Database
User.db

```sh
CREATE TABLE User ( Pawprint varchar(50), Name varchar(50), StudentId INT PRIMARY KEY NOT NULL, UserType INT, Password varchar(50));
```

Item.db

```sh
CREATE TABLE Item ( ItemId INT PRIMARY KEY NOT NULL, ItemName varchar(50), Status INT NOT NULL, Location varchar(50), BorrowTime datetime, ReturnTime datetime, BorrowLength int, Pawprint varchar(50));
```

## Entity Relationship Diagram
![alt text](https://github.com/YQ-Wang/CMP_SC3380-Final-Project/blob/master/ERD.png "ERD")

## CRUD
* We used created multiple times during the duration of our app. we used insert into on add item to the Item table. When user is getting enrolled, user will be added to the User table.
*	Read is the one we used most often, every error checking we need to use select statement to bind the value from the input. When we display tables, we used select statements. 
*	We used update when item was borrowed by a user. And in the item table, the status will be updated to 0 (unavailable) and the pawprint will be updated to the pawprint of the student who borrowed item. Also, when student returns the item, it will do the reverse.
*	We used deletion when admin is going to delete item. 
