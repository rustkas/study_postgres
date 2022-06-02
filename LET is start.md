Data store folder:
`E:\Program Files\PostgreSQL\9.5\data`

Доступ к консольному приложению Postgres:
`$ psql -U postgres`

Создание базы данных:
```
$ createdb --help
$ createdb -U postgres -e phpbook
```
Список баз данных:
```
$ psql -U postgres -l
phpbook=# \l
                                          Список баз данных
    Имя    | Владелец | Кодировка |     LC_COLLATE      |      LC_CTYPE       |     Права доступа
-----------+----------+-----------+---------------------+---------------------+-----------------------
 phpbook   | postgres | UTF8      | Russian_Russia.1251 | Russian_Russia.1251 |
 postgres  | postgres | UTF8      | Russian_Russia.1251 | Russian_Russia.1251 |
 template0 | postgres | UTF8      | Russian_Russia.1251 | Russian_Russia.1251 | =c/postgres          +
           |          |           |                     |                     | postgres=CTc/postgres
 template1 | postgres | UTF8      | Russian_Russia.1251 | Russian_Russia.1251 | =c/postgres          +
           |          |           |                     |                     | postgres=CTc/postgres
(4 строки)
```

Удаление базы данных:
`$ dropdb -e -U postgres phpbook`

Подключиться к базе данных:
`$ psql -U postgres phpbook`

Простые команды:
`phpbook=# SELECT 1+1;`
 
 ```
 ?column?
----------
        2
(1 строка)
```

Метаинформация о СУБД:

`phpbook=# \d pg_roles`

```
           Представление "pg_catalog.pg_roles"              
    Столбец     |           Тип            | Модификаторы   
----------------+--------------------------+--------------  
 rolname        | name                     |                
 rolsuper       | boolean                  |                
 rolinherit     | boolean                  |                
 rolcreaterole  | boolean                  |                
 rolcreatedb    | boolean                  |                
 rolcanlogin    | boolean                  |                
 rolreplication | boolean                  |                
 rolconnlimit   | integer                  |                
 rolpassword    | text                     |                
 rolvaliduntil  | timestamp with time zone |                
 rolbypassrls   | boolean                  |                
 rolconfig      | text[]                   |                
 oid            | oid                      |                
                                                            
phpbook=# \d pg_rules                                       
Представление "pg_catalog.pg_rules"                         
  Столбец   | Тип  | Модификаторы                           
------------+------+--------------                          
 schemaname | name |                                        
 tablename  | name |                                        
 rulename   | name |                                        
 definition | text |                                        
```                                                            


Для предсказуемой сортировки добавляйте суффиус "COLLATE C" к выполняемым командам 
(если порядок сортировки имеет значение)

Создание таблицы:
```
phpbook=# CREATE TABLE t_person(id int4, name varchar(10));
CREATE TABLE
phpbook=# \d t_person
           Таблица "public.t_person"
 Столбец |          Тип          | Модификаторы
---------+-----------------------+--------------
 id      | integer               |
 name    | character varying(10) |
```
