# Домашнее задание к занятию «Репликация и масштабирование. Часть 1»


### Задание 1

На лекции рассматривались режимы репликации master-slave, master-master, опишите их различия.

*Ответить в свободной форме.*

---
### Решение 1
Режимы репликации, такие как master-slave и master-master, используются в базах данных для обеспечения отказоустойчивости, масштабируемости и распределения нагрузки.
**Master-Slave (Мастер-Реплика):**

Основная конфигурация: Есть один главный сервер (мастер) и один или несколько подчиненных серверов (реплики).
Операции записи производятся только на мастере, в то время как операции чтения могут выполняться на любом из серверов (мастер или реплика). Реплики получают изменения из мастера и используются для чтения, что распределяет нагрузку и увеличивает производительность.
Отказоустойчивость: Если мастер выходит из строя, система может переключиться на одну из реплик, назначив ее новым мастером.
Может возникнуть проблема с задержкой репликации, когда данные на реплике могут быть неактуальными из-за задержки в передаче изменений от мастера.

**Master-Master (Мастер-Мастер):**

Основная конфигурация: Есть несколько мастер-серверов, каждый из которых может принимать как записывать, так и читать.
Оба мастера могут производить операции записи, что позволяет балансировать нагрузку между ними и увеличивать пропускную способность системы.
Отказоустойчивость: Если один из мастеров выходит из строя, другой мастер может продолжать принимать запросы на запись, обеспечивая отказоустойчивость и непрерывную доступность.
Синхронизация данных, могут возникать конфликты записей при одновременной записи в одни и те же данные.

---

### Задание 2

Выполните конфигурацию master-slave репликации, примером можно пользоваться из лекции.

*Приложите скриншоты конфигурации, выполнения работы: состояния и режимы работы серверов.*

### Решение 2

[docker-compose](https://github.com/sash3939/Replication1/assets/156709540/4d7e4961-c8ad-45fe-a249-ae636d89db86)
[my.cnf slave](https://github.com/sash3939/Replication1/assets/156709540/0a2fa39c-38dd-4fd9-b475-f2f11b75cb33)
[_my.cnf slave](https://github.com/sash3939/Replication1/assets/156709540/00d2cdc9-b19e-40fb-bdd0-9d4f39637c60)
[slave.sql](https://github.com/sash3939/Replication1/assets/156709540/5f1777df-7ca8-4282-a156-677f7a9e0cf6)
[master.sql](https://github.com/sash3939/Replication1/assets/156709540/f78fa4ad-5296-4ba0-9238-3ec1a5f6be59)
[_my.cnf master](https://github.com/sash3939/Replication1/assets/156709540/399dd5db-0405-4aaf-be0a-f16112d4136a)
[my.cnf master](https://github.com/sash3939/Replication1/assets/156709540/b4af030d-34f0-41d1-b553-fa2cd642da2a)

[docker ps](https://github.com/sash3939/Replication1/assets/156709540/a7a5d27d-12a8-4539-9849-9ecbf99166bd)

[created bd on master](https://github.com/sash3939/Replication1/assets/156709540/2b6edd66-0864-4887-9f83-4d83f1d0debf)

[SELECT from tables](https://github.com/sash3939/Replication1/assets/156709540/cc652eb5-fecb-41d6-b70c-daef57a9817c)

[MASTER STATUS](https://github.com/sash3939/Replication1/assets/156709540/c6f2ae2f-d5d1-4db2-a2e5-e9fbc27c45c0)
[MASTER STATUS on Slave](https://github.com/sash3939/Replication1/assets/156709540/c9601111-3433-4738-8624-6ca960c0e0b2)
[SLAVE STATUS on SLAVE](https://github.com/sash3939/Replication1/assets/156709540/8e64d4ae-adf7-4fec-a41b-3ca3691f6770)


---


## Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.

---

### Задание 3* 

Выполните конфигурацию master-master репликации. Произведите проверку.

*Приложите скриншоты конфигурации, выполнения работы: состояния и режимы работы серверов.*

### Решение 3*

[docker ps](https://github.com/sash3939/Replication1/assets/156709540/345263a0-718f-442e-b65a-cdc5626326a8)
[docker-compose](https://github.com/sash3939/Replication1/assets/156709540/69368a24-8237-4168-b910-24b1d7f66267)
[init_m1](https://github.com/sash3939/Replication1/assets/156709540/e3def70a-dd6e-4b3c-82c2-4ef3862420ba)
[my.cnf master1](https://github.com/sash3939/Replication1/assets/156709540/b4f3a289-939f-41ca-8830-448781b6b7c4)
[init_m2](https://github.com/sash3939/Replication1/assets/156709540/c1b61085-1941-4981-90cb-e9753c2cca8f)
[my.cnf master2](https://github.com/sash3939/Replication1/assets/156709540/a757d746-3fb7-4d2f-a534-3eb2fc12cc13)

[SELECT from tables](https://github.com/sash3939/Replication1/assets/156709540/e1355333-c562-41c6-97c5-d099e7270433)

[MASTER1 STATUS](https://github.com/sash3939/Replication1/assets/156709540/1ca8774b-e149-4062-becb-1ea16aa65641)
[MASTER2 STATUS](https://github.com/sash3939/Replication1/assets/156709540/2d79e59c-ec22-4c7b-967d-9e864797c590)

[SHOW DATABASES master2](https://github.com/sash3939/Replication1/assets/156709540/3f59f06e-66dd-4fae-8f3a-4d0fb78849d8)

[SELECT master2 after added columns](https://github.com/sash3939/Replication1/assets/156709540/20b54719-31bd-40a7-84b5-18906d538ba3)
[SELECT master1 after added on master2](https://github.com/sash3939/Replication1/assets/156709540/37eb59b4-a53b-4d3d-9d27-45088b3508a6)





