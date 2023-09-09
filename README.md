# TT_Hackathon sql database 
CREATE DATABASE Tiktok_Schema;

USE Tiktok_Schema;

CREATE TABLE seller
(sid int not null,
name varchar(50) not null,
CONSTRAINT s_pk PRIMARY KEY (sid));

CREATE TABLE product
(pid int not null,
name varchar(50) not null,
unit_price float not null,
available_units int not null,
CONSTRAINT p_pk PRIMARY KEY (pid));

CREATE TABLE product_seller
(sid int not null,
pid int not null,
CONSTRAINT ps_pk PRIMARY KEY (sid, pid),
CONSTRAINT ps_fk1 FOREIGN KEY(sid) REFERENCES seller(sid),
CONSTRAINT ps_fk2 FOREIGN KEY(pid) REFERENCES product(pid)); 

CREATE TABLE cart
(cid int not null,
CONSTRAINT c_pk PRIMARY KEY(cid));

CREATE TABLE user
(uid int not null,
name varchar(20) not null,
password varchar(20) not null,
email varchar(20) not null,
phone_number varchar(15) not null,
payment_detail varchar(20),
CONSTRAINT u_pk PRIMARY KEY(uid));

CREATE TABLE cart_product
(cart_id int not null,
user_id int not null,
product_id int not null,
product_quantity int not null,
CONSTRAINT cp_pk PRIMARY KEY(cart_id,user_id,product_id),
CONSTRAINT cp_fk1 FOREIGN KEY(cart_id) REFERENCES cart(cid),
CONSTRAINT cp_fk2 FOREIGN KEY(user_id) REFERENCES user(uid),
CONSTRAINT cp_fk3 FOREIGN KEY(product_id) REFERENCES product(pid));
