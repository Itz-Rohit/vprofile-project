# Prerequisites
#
- JDK 17 or 21
- Maven 3.9
- MySQL 8

# Technologies 
- Spring MVC
- Spring Security
- Spring Data JPA
- Maven
- JSP
- Tomcat
- MySQL
- Memcached
- Rabbitmq
- ElasticSearch
# Database
Here,we used Mysql DB 
sql dump file:
- /src/main/resources/db_backup.sql
- db_backup.sql file is a mysql dump file.we have to import this dump to mysql db server
- > mysql -u <user_name> -p accounts < db_backup.sql

# Architecture
┌─────────────┐
│   web01     │ (Nginx - Load Balancer/Reverse Proxy)
│ 192.168.56.11│ ← User Entry Point
└──────┬──────┘
       │
       ↓
┌─────────────┐
│   app01     │ (Tomcat - Application Server)
│ 192.168.56.12│
└──────┬──────┘
       │
       ├───────→ ┌─────────────┐
       │         │    mc01     │ (Memcached - Caching)
       │         │192.168.56.14│
       │         └─────────────┘
       │
       ├───────→ ┌─────────────┐
       │         │    rmq01    │ (RabbitMQ - Message Queue)
       │         │192.168.56.16│
       │         └─────────────┘
       │
       └───────→ ┌─────────────┐
                 │    db01     │ (MariaDB - Database)
                 │192.168.56.15│
                 └─────────────┘


