-- 1. Создайте базу из представленной картинки.
--    - У каждой таблицы должно быть поле id
--    - id автоинкрементальный и является первичным ключом

create table employees (
	id serial primary key,
	employee_name varchar (50) not null
)

create table employees_roles (
	id serial primary key,
	id_role int not null,
	id_employee int not null,
	foreign key (id_employee)
		references employees (id),
	foreign key (id_role)
		references roles (id)
)

create table roles (
	id serial primary key,
	role_title varchar (100) not null
)

create table salary (
	id serial primary key,
	monthly_salary int not null
)

create table roles_salary (
	id serial primary key,
	id_role int not null,
	id_salary int not null,
	foreign key (id_role)
		references roles (id),
	foreign key (id_salary)
		references salary (id)
)

create table Service (
	id serial primary key,
	service_title varchar (100) not null,
	price int not null
)

create table materials (
	id serial primary key,
	material_title varchar (100) not null,
	amount int not null,
	price int not null
)

create table claim (
	id serial primary key,
	service_id int not null,
	employee_id int not null,
	material_id int not null,
	claim_date date,
	sales_manager int not null,
	foreign key (employee_id)
		references employees (id),
	foreign key (sales_manager)
		references employees (id),
	foreign key (service_id)
		references Service (id),
	foreign key (material_id)
		references materials (id)
)

-- 2. Заполните таблицы данными. Не менее 10 строк в каждой таблице

-- Заполнение "employees"
insert into employees (employee_name)
values 
('James Padilla'), 
('Elaine Webb'), 
('Ashley Coleman'), 
('Kimberly Ellis'), 
('Steve Robinson,'),
('Michael Butler'),
('John Bailey'),
('George Banks'),
('Peter Medina'),
('Timothy Mann')

--select * from employees

-- Заполнение "employees_roles"
insert into employees_roles (id_role, id_employee)
values
(1, 2),
(2, 1),
(3, 4),
(4, 3),
(5, 6),
(6, 5),
(7, 8),
(8, 7),
(9, 10),
(10, 9)

--select * from employees_roles 

--Заполнение "roles"
insert into roles (role_title)
values 
('CEO'),
('Manager'),
('Seller'),
('Administrator'),
('Lawyer'),
('Seller'),
('Seller'),
('Accountant'),
('Cleaner'),
('Seller')

--select * from roles

-- Заполнение "salary"
insert into salary (monthly_salary)
values 
(4000),
(2000),
(1000),
(1500),
(3000),
(1000),
(1000),
(2000),
(500),
(1000)

--select * from salary

-- Заполнение "roles_salary"
insert into roles_salary (id_role, id_salary)
values
(1, 2),
(2, 1),
(3, 4),
(4, 3),
(5, 6),
(6, 5),
(7, 8),
(8, 7),
(9, 10),
(10, 9)

--select * from roles_salary

-- Заполнение "service"
insert into service (service_title, price)
values
('Building management systems', 934875),
('Energy generation, distribution and supply', 128879),
('Escalators and lifts', 238970),
('Facade engineering', 283979),
('Fire safety, detection and protection', 9207498),
('Air conditioning', 9203486),
('Lighting', 9283746),
('Lightning protection', 83235),
('Refrigeration', 346489),
('Security and alarm systems', 923781)

--select * from service

-- Заполнение "materials"
insert into materials (material_title, amount, price)
values
('Concrete', 123989767, 2),
('Wood', 1272341, 3.3),
('Steel', 2384678, 5),
('Plastic', 23876, 1.6),
('Stone', 238748, 3),
('Textiles', 234787, 6),
('Glass', 2137468, 8),
('Brick', 1278100, 3),
('Kevlar', 8233, 9),
('Bamboo', 3678, 7)

--select * from materials

-- Заполнение "claim"
insert into claim (service_id, employee_id, material_id, claim_date, sales_manager)
values
(1, 1, 1, CURRENT_DATE, 1),
(2, 2, 2, CURRENT_DATE, 2),
(3, 3, 3, CURRENT_DATE, 3),
(4, 4, 4, CURRENT_DATE, 4),
(5, 5, 5, CURRENT_DATE, 5),
(6, 6, 6, CURRENT_DATE, 6),
(7, 7, 7, CURRENT_DATE, 7),
(8, 8, 8, CURRENT_DATE, 8),
(9, 9, 9, CURRENT_DATE, 9),
(10, 10, 10, CURRENT_DATE, 10)

--select * from claim

TRUNCATE roles RESTART identity cascade;

-- 3. Добавить таблицу Suppliers с полями id, name

create table Suppliers (
	id serial primary key,
	name varchar (100) not null
)

-- 4. Добавить 10 строк поставщиков в таблицу Suppliers

insert into suppliers (name)
values
('Riforn'),
('Dehaus'),
('Aludecor'),
('ETM'),
('JBC'),
('Aqualtica'),
('Milore'),
('Maxwell'),
('STP'),
('UYN')

--select * from suppliers

-- 5. Обновить таблицу Materials. Добавить поле suplier_id которое связано с полем id в таблице Suppliers

alter table materials 
add suplier_id int,
add foreign key (suplier_id)
	references suppliers (id)
	
-- 6. Обновить таблицу Employees. Добавить varchar поле surname на 50 символов.	
	
alter table employees 
add surname varchar (50)

-- 7. Обновить таблицу Salary. Добавить varchar поле currency на 7 символов.

alter table salary 
add currency varchar (7)