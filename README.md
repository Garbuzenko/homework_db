# homework_db

Команды для создания БД
![База данных](https://u.netology.ngcdn.ru/backend/uploads/lms/tasks/homework_solutions/hashed_file/9/1678559/Untitled_Diagram.drawio.png)

***Вход в PSQL:

psql -U postgres 


***Создание БД:

CREATE DATABASE netology
    WITH 
    OWNER = postgres;

\q

***Вход в БД:

psql -U postgres -d netology

***Создание таблиц:

create table gener (
id serial primary key,
name varchar(50) unique
);

create table singer (
id serial primary key,
full_name varchar(100),
nick_name varchar(100), 
gener_id integer references gener(id)
);

create table albom (
id serial primary key,
name varchar(100), 
singer_id integer references singer(id),
year integer check(year > 1000 AND year < 2100)
);

create table track (
id serial primary key,
name varchar(100), 
singer_id integer references singer(id),
albom_id integer references albom(id),
time time
);