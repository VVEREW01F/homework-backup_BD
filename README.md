# Домашнее задание к занятию "Индексы" - `Bazylev Artem`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---


###Задание 1. Резервное копирование

1.1. Восстановление данных в полном объёме за предыдущий день:

    Полное резервное копирование: Создание копии всех данных базы данных за определенный период. Рекомендуется использовать ежедневные полные бэкапы для восстановления данных за предыдущий день.

1.2. Восстановление данных за час до предполагаемой поломки:

    Инкрементное резервное копирование: Создание копии данных, измененных с момента последнего бэкапа. Позволяет восстановить данные за определенный период, в данном случае - за последний час.

1.3.* Моментальное переключение на работающую или починенную базу данных:

    Использование технологий кластеризации и высокой доступности, таких как PostgreSQL Replication, MySQL Replication, или кластеры с автоматическим переключением (failover). Это обеспечивает непрерывную работу системы при сбоях, переключаясь на реплику или восстанавливая поврежденную базу.

###Задание 2. PostgreSQL

2.1. Пример команды резервирования данных и восстановления БД:

    Резервирование (pg_dump):

    bash

pg_dump -U username -h localhost -d dbname > backup.sql

Восстановление (pg_restore):

bash

    pg_restore -U username -h localhost -d dbname < backup.sql

2.1.* Автоматизация процесса:

    Да, процесс резервирования и восстановления в PostgreSQL можно автоматизировать с использованием сценариев на языке программирования (например, bash, Python) и планировщика задач cron для регулярного запуска pg_dump.

###Задание 3. MySQL

3.1. Пример команды инкрементного резервного копирования:

    Инкрементное резервное копирование с использованием mysqldump:

    bash

    mysqldump -u username -p --single-transaction --flush-logs --master-data=2 dbname > backup.sql

    Эта команда создаст инкрементный бэкап, который можно использовать для восстановления данных.

3.1.* Преимущество репликации по сравнению с обычным резервным копированием:

    Репликация MySQL позволяет создать точную копию основной базы данных на другом сервере. В случае сбоя основного сервера, переключение на реплику может быть более быстрым и эффективным, чем восстановление из регулярного бэкапа. Репликация также обеспечивает непрерывную доступность данных при сбоях.






