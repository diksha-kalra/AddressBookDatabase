# AddressBookDatabase

### UC1 Create Address Book Service Database
```
create database address_book_service;
show databases;
use address_book_service;
```

### UC2 Create Address Book Table in DB
```
create table address_book (
first_name   VARCHAR(20) NOT NULL,
last_name    VARCHAR(20) NOT NULL,
address      VARCHAR(50) NOT NULL,
city         VARCHAR(20) NOT NULL,
state        VARCHAR(20) NOT NULL,
zip          int(6) NOT NULL,
phone_number VARCHAR(15) NOT NULL,
email_id     VARCHAR(20) NOT NULL,
PRIMARY KEY  (first_name, last_name));
```

### UC3 Insert Contacts into Address Book Table
```
insert into address_book 
(first_name, last_name, address, city, state, zip, phone_number, email_id) VALUES
('james','cooper','dhundera','delhi','delhi',110019,9899151937,'james@gmail.com'),
('naman','kalra','thana','mumbai','mumbai',123456,9899151873,'naman@gmail.com'),
('annie','hathway','agra','agra','agra',343423,9899187937,annie@yahoo.com),
('ankit','dua','pamposh','delhi','delhi'123489,9878151873,'ankit@gmail.com');
```
```
select * from address_book;
```

### UC4 Edit Contact Using Name
```
update address_book set zip=121232 where first_name='ankit';
updtae address_book set address='malad' where first_name='naman';
```

### UC5 Delete Contact From Table Using Name
```
delete from address_book where first_name='naman' and last_name='kalra';
```

### UC6 Retrieve Person Belonging to City or State
```
select * from address_book where city='delhi' or state='delhi';
```

### UC7 Count Contacts by City and State
```
select city, count(first_name) from address_book group by city;
select state, count(first_name) from address_book group by state;
```

### UC8 Retrieve Sorted Entries by Person Name for given City
```
select * from address_book where city='delhi' order by first_name;
```

### UC9 Alter Address Book to add Name and Type
```
alter table address_book add address_book_name VARCHAR(20) NOT NULL;
alter table address_book add type VARCHAR(20) NOT NULL;
describe address_book;
update address_book set address_book_name='mycontacts' , type='friends' where first_name='ankit';
update address_book set address_book_name='mycontacts', type='family' where first_name='annie';
update address_book set address_book_name='mycontacts', type='profession' where first_name='james';
select * from address_book;
```

### UC10 Count Person in Address Book by Type
```
select type, count(first_name) from address_book group by type;
```

### UC11 Add person to both Friend and Family
```
alter table address_book drop PRIMARY KEY;
alter table address_book add PRIMARY KEY(first_name, last_name, type);
insert into address_book 
(first_name, last_name, address, city, state, zip, phone_number, email_id, address_book_name, type) VALUES
('deepali', 'garg', 'rohini','delhi',delhi',123231,9988131819,'deepali@gmail.com','mycontacts','family'),
('deepali', 'garg', 'rohini','delhi',delhi',123231,9988131819,'deepali@gmail.com','mycontacts','friends');
select * from address_book;
```

### UC13 Retrieve data from tables

#### inserting data into tables
```
insert into address_book_dict (address_book_name, address_book_type) VALUES
('mycontacts','family'),
('personal','professional');

insert into contact_details VALUES
('diksha','kalra','mycontacts','new delhi','delhi','delhi',110019,'9899151956,'kalra@gmail.com'),
('deepali','garg','personal','rohini','delhi','delhi',123123,'9899787878,'deepali@gmail.com');
```

#### retrieve data from tables
```
select * from contact_details where city='delhi';

select * from contact_details where state='delhi';

select * from contact_details where city='delhi' order by first_name;

select a.address_book_type, count(c.first_name) from address_book_dict a left join contact_details c 
on a.address_book_name=c.address_book_name group by a.address_book_type;
```
