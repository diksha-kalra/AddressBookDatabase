# AddressBookDatabase

### Create Address Book Service Database
```
create database address_book_service;
show databases;
use address_book_service;
```

### Create Address Book Table in DB
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

### Insert Contacts into Address Book Table
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

### Edit Contact Using Name
```
update address_book set zip=121232 where first_name='ankit';
updtae address_book set address='malad' where first_name='naman';
```

### Delete Contact From Table Using Name
```
delete from address_book where first_name='naman' and last_name='kalra';
```

### Retrieve Person Belonging to City or State
```
select * from address_book where city='delhi' or state='delhi';
```

