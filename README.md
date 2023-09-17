# Домашнее задание к занятию 12.08 - "`Резервное копирование баз данных`" - `Емельянов Михаил`

**Домашнее задание выполните в Google Docs или в md-файле в вашем репозитории GitHub.** 

Для оформления вашего решения в GitHub можете воспользоваться [шаблоном](https://github.com/netology-code/sys-pattern-homework).

Название файла должно содержать номер лекции и фамилию студента. Пример названия: «12.8. Резервное копирование баз данных — Александр Александров».

Перед тем как выслать ссылку, убедитесь, что её содержимое не является приватным, то есть открыто на просмотр всем, у кого есть ссылка. Если необходимо прикрепить дополнительные ссылки, просто добавьте их в свой Google Docs.

Любые вопросы по решению задач задавайте в чате учебной группы.

---

### Задание 1. Резервное копирование

### Кейс
Финансовая компания решила увеличить надёжность работы баз данных и их резервного копирования. 

Необходимо описать, какие варианты резервного копирования подходят в случаях: 

1.1. Необходимо восстанавливать данные в полном объёме за предыдущий день.

1.2. Необходимо восстанавливать данные за час до предполагаемой поломки.

1.3.* Возможен ли кейс, когда при поломке базы происходило моментальное переключение на работающую или починенную базу данных.

*Приведите ответ в свободной форме.*

#### ОТВЕТ:

1.1. Необходимо выполнять полное резервное копирование раз в неделю. А раз в день дифференциальный бэкап. Для восстановления данных в полном объеме за заданный день нужно будет восстановить полный бэкап на начало недели и на него накатить тот дифференциальный бэкап за тот день, за который нужно восстановить данные.

1.2. В этом случае как и в первом основой является полный бэкап но уже раз в день (в нерабочее время, когда операции не происходят или нагрузка снижена). А с необходимой частотой (в нашем случае раз в час) осуществляется инкрементный бэкап. Для восстановления данных необходимо восстановить нанные на начало дня полным бэкапом, а далее поочередно накатывать инкрементные бэкапы до того искомого часа.

1.3. Данный кейс возможен в рамках репликации а не резервного копирования. При обрушении мастера слейв, хранящий последние реплицированные данные, переводится в режим мастера руками (медленно) или автоматически (скриптом и быстро).

---

### Задание 2. PostgreSQL

2.1. С помощью официальной документации приведите пример команды резервирования данных и восстановления БД (pgdump/pgrestore).

2.1.* Возможно ли автоматизировать этот процесс? Если да, то как?

*Приведите ответ в свободной форме.*

#### ОТВЕТ:

2.1. Выгрузка базы данных в специальном формате:
```
$ pg_dump -Fc mydb > db.dump
```
-F format
Указывает формат вывода копии. format может принимать следующие значения: 
c
*custom*
Выгрузить данные в специальном архивном формате, пригодном для дальнейшего использования утилитой pg_restore. Наряду с форматом directory является наиболее гибким форматом, позволяющим вручную выбирать и сортировать восстанавливаемые объекты. Вывод в этом формате по умолчанию сжимается.

---

### Задание 3. MySQL

3.1. С помощью официальной документации приведите пример команды инкрементного резервного копирования базы данных MySQL. 

3.1.* В каких случаях использование реплики будет давать преимущество по сравнению с обычным резервным копированием?

*Приведите ответ в свободной форме.*

#### ОТВЕТ:



---

Задания, помеченные звёздочкой, — дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.
