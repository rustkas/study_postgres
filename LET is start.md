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

Удалить таблицу:
DROP TABLE t_person;


Удалить таблицу:

`DROP TABLE t_person;`

Выполнить код из файла:

```
[E:\work\soft\cmder]psql -U postgres -e phpbook < E:\Users\tol_pc\Desktop\postgresql\b1\ch06\code.sql
CREATE TABLE t_person(id serial,
                        name text,
                        zip_code int4,
                        city text,
                                PRIMARY KEY (id));
CREATE TABLE
CREATE TABLE t_children(id serial,
                        pers_id int4,
                        name text,
                                PRIMARY KEY (id));
CREATE TABLE


[E:\work\soft\cmder]
```
Выполнить код из файла:
```
psql -U postgres -e phpbook < E:\Users\tol_pc\Desktop\postgresql\b1\ch06\code.sql

DROP TABLE t_person;
DROP TABLE t_children;
```

Добавление комментация к таблице:

Подключиться к базе данных:
```
$ psql -U postgres phpbook
COMMENT ON TABLE t_person IS 'Это комментарий к таблице';
COMMENT ON COLUMN t_person.zip_code IS 'This is a zip code';
```

Пример простой команды INSERT:

`psql -U postgres -e phpbook < E:\Users\tol_pc\Desktop\postgresql\b1\ch06\insert_into_t_person.sql`


```
INSERT INTO t_person (name, zip_code, city) VALUES ('Hans',1150,'Vienna');
INSERT INTO t_person (name, zip_code) VALUES ('Epl',1060);
```
SELECT
```
SELECT * FROM t_person;
SELECT city, id, name, zip_code FROM t_person;
SELECT t_person.* FROM t_person;

```

#### WHERE

`SELECT city, id, name, zip_code FROM t_person WHERE id=1;`

#### Вставка специальных символов

`INSERT INTO t_person (name) VALUES ('o''Connor'); SELECT * FROM t_person;`


#### Обработка значений NULL

```
SELECT 
  id,
  name,
  zip_code,
  city
FROM 
  public.t_person
WHERE  public.t_person.city IS NULL;
```
```
SELECT 
  id,
  name,
  zip_code,
  city
FROM 
  public.t_person
WHERE  public.t_person.city = '';
```

Это выражение не даёт правильный результат:

```
SELECT 
  id,
  name,
  zip_code,
  city
FROM 
  public.t_person
WHERE  public.t_person.city = NULL;
```

Ставные условия

`SELECT city, id, name, zip_code FROM t_person WHERE zip_code=1150 AND city='Vienna';`

`SELECT city, id, name, zip_code FROM t_person WHERE zip_code=1150 AND id=1;`

`SELECT city, id, name, zip_code FROM t_person WHERE zip_code=1150 AND id>=1;`

`SELECT city, id, name, zip_code FROM t_person WHERE name='Hans' OR name='Epl';`

`SELECT city, id, name, zip_code FROM t_person WHERE (name='Hans' OR name='Epl') AND city='Vienna';`

Следующая запись приведёт к тому же результату:

`SELECT city, id, name, zip_code FROM t_person WHERE name='Hans' OR (name='Epl' AND city='Vienna');`

### Форматирование вывода
```
SELECT 'Hello World!' AS "info";

SELECT name || 'lives in ' || city FROM t_person WHERE id=1;
SELECT name || ' lives in ' || city FROM t_person  WHERE id=1;
SELECT name || ' lives in ' || city AS 'caption' FROM t_person  WHERE name || ' lives in ' || city='Hans lives in Vienna';
SELECT name || ' lives in ' || city AS caption FROM t_person  WHERE name || ' lives in ' || city='Hans lives in Vienna';

#### LIMIN и OFFSET
```
SELECT * FROM t_person;
SELECT * FROM t_person LIMIT 2;
SELECT * FROM t_person LIMIT 2 OFFSET 1;
```

#### Временные таблицы
```
CREATE TEMPORARY TABLE tmp_data(id integer, data text);
SELECT * FROM tmp_data;
INSERT INTO tmp_data (id, data) VALUES (1,'one');
INSERT INTO tmp_data (id, data) VALUES (2,'two');
INSERT INTO tmp_data (id, data) VALUES (3,'three');
INSERT INTO tmp_data (id, data) VALUES (4,'four');
INSERT INTO tmp_data (id, data) VALUES (5,'five');
SELECT * FROM tmp_data;
```

```
DROP TABLE tmp_data;
```

Временные таблицы и значение типа serial


CREATE TEMPORARY TABLE tmp_data(id serial, data text);
INSERT INTO tmp_data (data) VALUES ('one');
INSERT INTO tmp_data (data) VALUES ('two');
INSERT INTO tmp_data (data) VALUES ('three');
INSERT INTO tmp_data (data) VALUES ('four');
INSERT INTO tmp_data (data) VALUES ('five');
SELECT * FROM tmp_data;

#### SELECT INTO

```
SELECT *FROM t_person;
SELECT * INTO TEMPORARY TABLE tmp_person FROM t_person;
SELECT * FROM tmp_person;
```
#### Обновление и удаление

\h UPDATE

DO backup:

```
SELECT * INTO TEMPORARY TABLE tmp_person FROM t_person;
```

```
UPDATE t_person SET city='Mauerbach' WHERE id=2;
SELECT * FROM t_person WHERE id=2;
DELETE FROM t_person WHERE id>3;
```

#### \h TRUNCATE

```
TRUNCATE TABLE t_person RESTART IDENTITY;
SELECT * FROM t_person;
```

Restore from backup:
```
INSERT INTO t_person SELECT * FROM tmp_person;
```
