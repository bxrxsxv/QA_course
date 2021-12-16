### Примеры заданий

---
Вывести пользователей которые были созданы 2021-07-12 00:00:00 и у которых в имени есть слово Andrey

```sql
select * from qa_users
where created_on='2021-07-12 00:00:00' and username like '%Andrey%';
```

---

Вывести имена и зарплаты Junior специалистов  

```sql
select employee_name, monthly_salary
from employees
join employees_salary
on employees.id = employees_salary.employee_id
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id 
where role_name like '%Junior%';
```

---
```sql
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
```
---

### Здесь можно ознакомиться подробнее с выполненными заданиями по SQL

[SELECT](https://github.com/bxrxsxv/QA_course/tree/SQL/HW_1) |
[JOIN](https://github.com/bxrxsxv/QA_course/tree/SQL/HW_2) |
[DDL](https://github.com/bxrxsxv/QA_course/tree/SQL/HW_3)
