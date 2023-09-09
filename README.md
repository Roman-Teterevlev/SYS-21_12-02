Roman Teterevlev

Работа с данными (DDL/DML)

### Задание 1
1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.

1.2. Создайте учётную запись sys_temp. 

1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)

1.4. Дайте все права для пользователя sys_temp. 

1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

1.6. Переподключитесь к базе данных от имени sys_temp.

Для смены типа аутентификации с sha2 используйте запрос: 
```sql
ALTER USER 'sys_test'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```
1.6. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.

1.7. Восстановите дамп в базу данных.

1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)

*Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.*

### Ответ:

![alt text](https://github.com/Roman-Teterevlev/SYS-21_12-02/blob/main/12-02_1.1.png)

![alt text](https://github.com/Roman-Teterevlev/SYS-21_12-02/blob/main/12-02_1.2.png)

![alt text](https://github.com/Roman-Teterevlev/SYS-21_12-02/blob/main/12-02_1.3.1.png)

![alt text](https://github.com/Roman-Teterevlev/SYS-21_12-02/blob/main/12-02_1.3.2.png)

![alt text](https://github.com/Roman-Teterevlev/SYS-21_12-02/blob/main/12-02_1.4.png)

![alt text](https://github.com/Roman-Teterevlev/SYS-21_12-02/blob/main/12-02_1.5.1.png)

![alt text](https://github.com/Roman-Teterevlev/SYS-21_12-02/blob/main/12-02_1.5.2.png)

![alt text](https://github.com/Roman-Teterevlev/SYS-21_12-02/blob/main/12-02_1.6.png)

![alt text](https://github.com/Roman-Teterevlev/SYS-21_12-02/blob/main/12-02_1.8.png)

```
CREATE USER 'sys_temp'@'localhost' IDENTIFIED BY '123456';

SELECT User FROM mysql.user;

GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'localhost';

FLUSH PRIVILEGES;

SHOW GRANTS FOR 'sys_temp'@'localhost';

ALTER USER 'sys_temp'@'localhost' IDENTIFIED WITH mysql_native_password BY 'SYS-21';
```

### Задание 2
Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. Пример: (скриншот/текст)
```
Название таблицы | Название первичного ключа
customer         | customer_id
```
### Ответ:

```
Название таблицы           |         Название первичного ключа
category                   |         category_id
country                    |         country_id
store                      |         store_id
film                       |         film_id
film_category              |         film_id
                           |         category_id
film_text                  |         film_id
actor                      |         actor_id
film_actor                 |         actor_id
                           |         film_id
inventory                  |         inventory_id
address                    |         address_id
customer                   |         customer_id
rental                     |         rental_id
city                       |         city_id
staff                      |         staff_id
payment                    |         payment_id
language                   |         language_id
staff_list                 |         -
customer_list              |         -
sales_by_film_category     |         -
sales_by_store             |         -
actor_info                 |         -
film_list                  |         -
nicer_but_slower_film_list |         -
```

## Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.

### Задание 3*
3.1. Уберите у пользователя sys_temp права на внесение, изменение и удаление данных из базы sakila.

3.2. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

*Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.*

### Ответ:

![alt text](https://github.com/Roman-Teterevlev/SYS-21_12-02/blob/main/12-02_3.1.png)

![alt text](https://github.com/Roman-Teterevlev/SYS-21_12-02/blob/main/12-02_3.2.png)

```
SHOW GRANTS FOR 'sys_temp'@'localhost';

REVOKE INSERT, UPDATE, DELETE ON *.* FROM 'sys_temp'@'localhost';

SHOW GRANTS FOR 'sys_temp'@'localhost';
```

