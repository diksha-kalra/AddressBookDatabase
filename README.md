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
zip          long NOT NULL,
phone_number long NOT NULL,
email_id     VARCHAR(20) NOT NULL,
PRIMARY KEY  (first_name, last_name));
```
