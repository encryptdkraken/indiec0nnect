# indiec0nnect
Create database indieconnect; 

use indieconnect; 

 

Create table Employees ( 

Emp_ID Int Not Null auto_increment, 

Emp_Displayname varchar(20) not null,  

 Emp_first varchar(10) not null,  

Emp_last varchar(15) not null, 

Emp_Email varchar(50) not null, 

Primary key (Emp_ID) ); 

Insert into Employees (Emp_Displayname, Emp_first, Emp_last, Emp_Email) values (‘TailPipeOne’, ‘Cameron’, ‘McLaughlin’, ‘Cameron.McLaughlin@indieconnect.com’); 

Insert into Employees (Emp_Displayname, Emp_first, Emp_last, Emp_Email) values (‘Fafito’, ‘Rafael’, ‘Martinez’, ‘rafael.martinez@indieconnect.com’); 

Insert into Employees (Emp_Displayname, Emp_first, Emp_last, Emp_Email) values (’Krogers721’, ’Kameron’, ’Rogers’, ’Rogers.kameron@indieconnect.com’); 

Insert into Employees (Emp_Displayname, Emp_first, Emp_last, Emp_Email) values ('Felipe123','Felipe','Dacunha', 'Felipe.Dacunha@indieconnect.com'); 

 

Create table Users  ( 

User_ID int not null auto_increment, 

User_DisplayName varchar(30) not null, 

User_First varchar(30) not null,  

User_Last Varchar(15) Not Null,  

User_Email Varchar(50) Not Null, 

User_DOB  Date Not Null, 

Primary key (User_Id) 

); 

insert into users (User_displayname, user_first, User_last, User_email, user_DOB) values ( 'PaintLover123', 'Bob', 'Ross', 'paint_lover123@aol.com', '1/2/1990'); 

insert into users (User_displayname, user_first, User_last, User_email, user_DOB) values ( 'Independenceguy', 'Thomas', 'Jefferson', 'Tom.jeffer1776@aol.com', '3/6/1720') 

); 

 

 

Create table Publisher ( 

Pub_ID Int Not Null Auto_increment, 

Pub_Company Varchar(25) Not Null, 

Pub_Website Varchar(50) Not Null) 

); 

 

Create table Developers (Dev_ID Int Not Null Auto_increment, 

Dev_Company Varchar (25), 

Dev_First Varchar (10) Not Null,  

Dev_Last Varchar (15) Not Null, 

Dev_Website Varchar (50) Not Null, Pub_ID Int,  

Primary key (Dev_ID), 

Foreign key (Pub_ID), references Publisher (Pub_ID) 

ON DELETE CASCADE 
ON UPDATE CASCADE 

); 

 

 

Create table Games ( 

Game_ID Int Not Null Auto_increment,  

Game_Title Varchar (25) Not Null,  

Game_Rating List('E','T','MA','RP'),  

Game_score Decimal(2,1),  

Game_ReleaseDate Date Not Null,  

Game_EarlyAccess List('Yes','No') Not Null , 

Game_Price Decimal(2,2) , 

Game_Released List('Yes','No') Not Null , 

Dev_ID Int Not Null , 

Pub_ID Int , 

Primary key (Game_Id), 

Foreign key (Dev_ID) references Developers (Dev_ID) 

ON DELETE CASCADE 
ON UPDATE CASCADE, 

Foreign key (Pub_ID) references Publisher (Pub_ID) 

ON DELETE CASCADE 
ON UPDATE CASCADE 

); 

 

Create table Edits ( 

-- Edit_ID int not null auto_increment, 

Edit_ID SERIAL, 

Edit_TimeStamp timestamp not null, 
Edit_type ENUM('Update','Remove','Add'), 
Emp_ID Int not null, 
Game_ID Int Not Null, 

-- Primary key (Edit_ID), 

Foreign key (Emp_ID) references Employees (Emp_ID) 

ON DELETE CASCADE 

ON UPDATE CASCADE, 

Foreign key (Game_ID) references Games (Game_ID) 

ON DELETE CASCADE 

ON UPDATE CASCADE 

); 
