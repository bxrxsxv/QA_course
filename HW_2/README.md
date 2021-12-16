### SQL HomeWork 2. Joins
```sh
Подключится к 
Host: 159.69.151.133
Port: 5056
DB: qa_db_2
User: user_22_x
Pass: *****
```
---

1. Вывести всех работников чьи зарплаты есть в базе, вместе с зарплатами.

```sql
select employee_name, monthly_salary 
from employees
join employees_salary 
on employees.id = employees_salary.employee_id;
```

2. Вывести всех работников у которых ЗП меньше 2000.

```sql
select employee_name, monthly_salary 
from employees
join employees_salary
on employees.id = employees_salary.employee_id 
where monthly_salary < 2000;
```

3. Вывести все зарплатные позиции, но работник по ним не назначен. (ЗП есть, но не понятно кто её получает.)

```sql
select employee_name, monthly_salary 
from employees
right join employees_salary
on employees.id = employees_salary.employee_id
where employee_name is null;
```

4. Вывести все зарплатные позиции  меньше 2000 но работник по ним не назначен. (ЗП есть, но не понятно кто её получает.)

```sql
select employee_name, monthly_salary 
from employees
right join employees_salary 
on employees.id = employees_salary.employee_id
where monthly_salary < 2000 and employee_name is null;
```

5. Найти всех работников кому не начислена ЗП.

```sql
select employee_name, monthly_salary 
from employees
left join employees_salary
on employees.id = employees_salary.employee_id
where monthly_salary is null;
```

6. Вывести всех работников с названиями их должности.

```sql
select employee_name, role_name
from employees
full join roles_employees
on employees.id = roles_employees.employee_id
left join roles
on role_id = roles.id;
```

7. Вывести имена и должность только Java разработчиков.

```sql
select employee_name, role_name
from employees
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id
where role_name like '%Java %';
```

8. Вывести имена и должность только Python разработчиков.

```sql
select employee_name, role_name
from employees
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id
where role_name like '%Python %';
```

9. Вывести имена и должность всех QA инженеров.

```sql
select employee_name, role_name
from employees
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id
where role_name like '%QA%';
```

10. Вывести имена и должность ручных QA инженеров.

```sql
select employee_name, role_name
from employees
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id
where role_name like '%Manual QA%';
```

11. Вывести имена и должность автоматизаторов QA

```sql
select employee_name, role_name
from employees
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id
where role_name like '%Automation QA%';
```

12. Вывести имена и зарплаты Junior специалистов

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

13. Вывести имена и зарплаты Middle специалистов

```sql
select employee_name, monthly_salary
from employees
join employees_salary
on employees.id = employees_salary.employee_id
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id 
where role_name like '%Middle%';
```

14. Вывести имена и зарплаты Senior специалистов

```sql
select employee_name, monthly_salary
from employees
join employees_salary
on employees.id = employees_salary.employee_id
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id 
where role_name like '%Senior%';
```

15. Вывести зарплаты Java разработчиков

```sql
select employee_name, monthly_salary
from employees
join employees_salary
on employees.id = employees_salary.employee_id
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id 
where role_name like '%Java %';
```

16. Вывести зарплаты Python разработчиков

```sql
select employee_name, monthly_salary
from employees
join employees_salary
on employees.id = employees_salary.employee_id
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id 
where role_name like '%Python%';
```

17. Вывести имена и зарплаты Junior Python разработчиков

```sql
select employee_name, monthly_salary
from employees
full join employees_salary
on employees.id = employees_salary.employee_id
full join roles_employees
on employees.id = roles_employees.employee_id
full join roles
on role_id = roles.id 
where role_name like '%Junior Python%';
```

18. Вывести имена и зарплаты Middle JS разработчиков

```sql
select employee_name, monthly_salary
from employees
join employees_salary
on employees.id = employees_salary.employee_id
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id 
where role_name like '%Middle JavaScript%';
```

19. Вывести имена и зарплаты Senior Java разработчиков

```sql
select employee_name, monthly_salary
from employees
join employees_salary
on employees.id = employees_salary.employee_id
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id 
where role_name like '%Senior Java %';
```

20. Вывести зарплаты Junior QA инженеров

```sql
select employee_name, monthly_salary
from employees
join employees_salary
on employees.id = employees_salary.employee_id
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id 
where role_name like '%Junior%QA%';
```

21. Вывести среднюю зарплату всех Junior специалистов

```sql
select avg(monthly_salary) as avgsalaryjunior
from employees
join employees_salary
on employees.id = employees_salary.employee_id
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id 
where role_name like '%Junior%';
```

22. Вывести сумму зарплат JS разработчиков

```sql
select sum(monthly_salary) as sumsalaryjs
from employees
join employees_salary
on employees.id = employees_salary.employee_id
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id 
where role_name like '%JavaS%';
```

23. Вывести минимальную ЗП QA инженеров

```sql
select min(monthly_salary) as minsalaryqa
from employees
join employees_salary
on employees.id = employees_salary.employee_id
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id 
where role_name like '%QA%';
```

24. Вывести максимальную ЗП QA инженеров

```sql
select max(monthly_salary) as maxsalaryqa
from employees
join employees_salary
on employees.id = employees_salary.employee_id
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id 
where role_name like '%QA%';
```

25. Вывести количество QA инженеров

```sql
select count(role_name) as countqa
from employees
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id 
where role_name like '%QA%';
```

26. Вывести количество Middle специалистов.

```sql
select count(role_name) as countmiddle
from employees
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id 
where role_name like '%Middle%';
```

27. Вывести количество разработчиков

```sql
select count(role_name) as countmiddle
from employees
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id 
where role_name like '%developer%';
```

28. Вывести фонд (сумму) зарплаты разработчиков.

```sql
select sum(monthly_salary) as sumsalaryjs
from employees
join employees_salary
on employees.id = employees_salary.employee_id
join roles_employees
on employees.id = roles_employees.employee_id
join roles
on role_id = roles.id 
where role_name like '%developer%';
```

29. Вывести имена, должности и ЗП всех специалистов по возрастанию

```sql
select employee_name, role_name, monthly_salary
from employees
left join employees_salary
on employees.id = employees_salary.employee_id
left join roles_employees
on employees.id = roles_employees.employee_id
left join roles
on role_id = roles.id
order by monthly_salary
```

30. Вывести имена, должности и ЗП всех специалистов по возрастанию у специалистов у которых ЗП от 1700 до 2300

```sql
select employee_name, role_name, monthly_salary
from employees
left join employees_salary
on employees.id = employees_salary.employee_id
left join roles_employees
on employees.id = roles_employees.employee_id
left join roles
on role_id = roles.id
where monthly_salary between 1700 and 2300
order by monthly_salary;
```

31. Вывести имена, должности и ЗП всех специалистов по возрастанию у специалистов у которых ЗП меньше 2300

```sql
select employee_name, role_name, monthly_salary
from employees
left join employees_salary
on employees.id = employees_salary.employee_id
left join roles_employees
on employees.id = roles_employees.employee_id
left join roles
on role_id = roles.id
where monthly_salary < 2300
order by monthly_salary;
```

32. Вывести имена, должности и ЗП всех специалистов по возрастанию у специалистов у которых ЗП равна 1100, 1500, 2000

```sql
select employee_name, role_name, monthly_salary
from employees
join employees_salary
on employees.id = employees_salary.employee_id
left join roles_employees
on employees.id = roles_employees.employee_id
left join roles
on role_id = roles.id
where monthly_salary in (1100, 1500, 2000)
order by monthly_salary;
```
