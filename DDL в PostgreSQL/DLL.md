## DLL
[Исходный код](https://github.com/charmwizwsh/databases/blob/alpha/DDL%20%D0%B2%20PostgreSQL/%D0%98%D1%81%D1%85%D0%BE%D0%B4%D0%BD%D1%8B%D0%B9%20%D1%81%D0%BA%D1%80%D0%B8%D0%BF%D1%82.txt)

1. Создание БД

CREATE DATABASE Dealer;

2. Создание табличного пространства и роли.
CREATE TABLESPACE DealerTS location 'var/lib/postgresql';
ALTER DATABASE Dealer SET TABLESPACE DealerTS;
CREATE ROLE Role1 with CREATEDB CREATEROLE ;
CREATE USER User1 WITH PASSWORD 'pass';

3. Схемы данных
CREATE SCHEMA Cars;
CREATE SCHEMA Persons;

4. Таблицы проекта

CREATE TABLE cars.Car
(
  car_id   INTEGER NOT NULL ,
  vin      VARCHAR NULL     ,
  von      VARCHAR NOT NULL ,
  year     INTEGER NOT NULL ,
  model_id INTEGER NOT NULL ,
  PRIMARY KEY (car_id)
);

CREATE TABLE cars.Doc
(
  doc_id      INTEGER NOT NULL ,
  doc_no      VARCHAR NOT NULL ,
  doc_dt      DATE    NULL     ,
  car_id      INTEGER NOT NULL ,
  price       NUMERIC NOT NULL ,
  person_id   INTEGER NULL     ,
  employee_id INTEGER NULL     ,
  PRIMARY KEY (doc_id)
) ;

CREATE TABLE persons.Email
(
  person_id INTEGER NOT NULL ,
  Email     VARCHAR NOT NULL ,
  is_main   BOOL    NOT NULL ,
  PRIMARY KEY (person_id, Email)
) ;

CREATE TABLE persons.Employee
(
  person_id INTEGER NOT NULL ,
  login     VARCHAR NOT NULL ,
  pass      VARCHAR NOT NULL ,
  PRIMARY KEY (person_id)
) ;

CREATE TABLE persons.Gender
(
  gender_id INTEGER NOT NULL ,
  gender_cd VARCHAR NOT NULL ,
  gender_nm VARCHAR NULL     ,
  PRIMARY KEY (gender_id)
) ;

CREATE TABLE persons.Legal_person
(
  person_id     INTEGER NOT NULL ,
  name          VARCHAR NOT NULL ,
  inn           INTEGER NULL     ,
  kpp           INTEGER NULL     ,
  legal_address VARCHAR NULL     ,
  repr_id       INTEGER NOT NULL ,
  PRIMARY KEY (person_id)
) ;

CREATE TABLE cars.Model
(
  model_id   INTEGER NOT NULL ,
  model_cd   VARCHAR NOT NULL ,
  model_nm   VARCHAR NULL     ,
  generation INTEGER NULL     ,
  brand_id   INTEGER NOT NULL ,
  PRIMARY KEY (model_id)
) ;

CREATE TABLE persons.Natural_person
(
  person_id  INTEGER NOT NULL ,
  surname    VARCHAR NULL     ,
  name       VARCHAR NOT NULL ,
  patronymic VARCHAR NULL     ,
  birth_dt   DATE    NULL     ,
  address    VARCHAR NULL     ,
  gender_id  INTEGER NOT NULL ,
  PRIMARY KEY (person_id)
) ;

CREATE TABLE persons.Person
(
  person_id      INTEGER NOT NULL ,
  person_type_id INTEGER NOT NULL ,
  PRIMARY KEY (person_id)
) ;

CREATE TABLE persons.Person_type
(
  person_type_id INTEGER NOT NULL ,
  person_type_cd VARCHAR NOT NULL ,
  person_type_nm VARCHAR NULL     ,
  PRIMARY KEY (person_type_id)
) ;

CREATE TABLE persons.Phone
(
  person_id INTEGER NOT NULL ,
  phone     INTEGER NOT NULL ,
  is_main   BOOL    NOT NULL ,
  is_owner  BOOL    NOT NULL ,
  PRIMARY KEY (person_id, phone)
) ;

