# Часть 1: Работа с текстом
1) Вывести список имен пользователей из файла /etc/passwd
2) В домашней директории создать каталог text_processing
3) В директории text_processing создать файл syslog с содержимым
```
# Cron logs
Oct 20 06:24:01 server1 CRON[1349677]: (user1) CMD (   /usr/bin/python3 /home/user1/update.py)
Oct 20 06:25:01 server3 CRON[1349678]: (user2) CMD (   /usr/bin/python3 /home/user2/report.py)
Oct 20 06:26:01 server2 CRON[1349679]: (root) CMD (   /usr/bin/cleanup.sh)
Oct 20 06:27:01 server3 CRON[1349680]: (user3) CMD (   /usr/bin/backup.sh)
Oct 20 06:28:01 server1 CRON[1349681]: (user4) CMD (   /usr/bin/monitor.sh)

# Error logs
Oct 20 06:30:00 server1 sshd[12345]: Failed password for invalid user admin from 192.168.0.10 port 22 ssh2
Oct 20 06:31:00 server3 sshd[12346]: Failed password for invalid user guest from 192.168.0.11 port 22 ssh2
Oct 20 06:32:00 server1 sshd[12347]: Accepted password for user2 from 192.168.0.12 port 22 ssh2
Oct 20 06:33:00 server1 sshd[12348]: Failed password for invalid user test from 192.168.0.13 port 22 ssh2

# Warning logs
Oct 20 06:35:00 server1 kernel: [123456] Warning! CPU temperature is high.
Oct 21 09:10:00 server2 kernel: [123458] Warning! High CPU usage detected on process ID 5678.
Oct 21 09:11:00 server2 systemd[1]: Warning! Service myservice.service is taking too long to start.
Oct 21 09:12:00 server2 sshd[23461]: Warning! Multiple failed login attempts from 192.168.0.25.
Oct 21 09:13:00 server2 application[34571]: Warning! Disk space on /home is below 10% remaining.

# Info logs
Oct 21 09:02:00 server2 application[34569]: INFO User1 logged in successfully.
Oct 21 09:03:00 server2 application[34570]: INFO User3 logged out.
Oct 21 09:14:00 server2 application[34572]: INFO User4 logged in successfully from 192.168.0.26.
Oct 21 09:15:00 server2 application[34573]: INFO Backup completed successfully at /backup/user4_backup.tar.gz.
Oct 21 09:16:00 server2 systemd[1]: INFO Service myservice.service started successfully.
Oct 21 09:17:00 server2 sshd[23462]: INFO User1 logged out from session on terminal pts/0.
```
4) В файле syslog найти все записи, которые содержат application
5) В файле syslog найти записи о запусках cron на сервере server3 и вывести команду, которая запускалась (это то, что в скобках в конце)
6) В файле syslog найти все записи, содержащие ssh и вывести для них название сервера
7) В файле syslog найти все записи, содержащие "Failed password" и вывести только ip
8) В файле syslog найти записи, содержащие "Accepted password" и вывести имя пользователя и ip
9) В директории text_proxessing создать файл logs.log с содержимым
```
2024-10-27 08:15:23 INFO [Server] Application started successfully
2024-10-27 08:17:45 DEBUG [UserService] User login attempt: john_doe@example.com
2024-10-27 08:17:46 INFO [UserService] User john_doe@example.com logged in successfully
2024-10-27 08:20:12 WARN [DatabaseService] High database load detected
2024-10-27 08:22:30 ERROR [PaymentService] Transaction failed for user: alice@example.com
2024-10-27 08:22:31 INFO [PaymentService] Retrying transaction for alice@example.com
2024-10-27 08:22:32 INFO [PaymentService] Transaction successful for alice@example.com
2024-10-27 08:25:00 DEBUG [CacheService] Cache hit ratio: 0.75
2024-10-27 08:35:15 INFO [BackupService] Daily backup started
2024-10-27 08:35:22 ERROR [NetworkService] Connection timeout: 192.168.1.105
2024-10-27 08:35:25 WARN [NetworkService] Retrying connection to 192.168.1.105
2024-10-27 08:35:30 INFO [NetworkService] Connection established with 192.168.1.105
2024-10-27 08:40:00 DEBUG [MemoryManager] Current memory usage: 2.5GB
2024-10-27 08:45:12 INFO [UpdateService] Checking for system updates
2024-10-27 08:45:15 INFO [UpdateService] No new updates available
2024-10-27 08:50:30 WARN [SecurityService] Multiple failed login attempts for user: eve@example.com
2024-10-27 08:50:35 ERROR [SecurityService] Account locked: eve@example.com
2024-10-27 08:55:00 INFO [MonitoringService] All systems operating normally
2024-10-27 09:00:00 INFO [SchedulerService] Running hourly tasks
2024-10-27 09:05:23 DEBUG [APIService] API request received from 10.0.0.15
2024-10-27 09:05:24 ERROR [APIService] Invalid API key from 10.0.0.15
2024-10-27 09:10:00 INFO [LoadBalancer] Traffic distribution: Server1: 40%, Server2: 35%, Server3: 25%
2024-10-27 09:15:30 WARN [DiskService] Low disk space on /dev/sda1: 85% used
2024-10-27 09:20:00 INFO [BackupService] Daily backup completed successfully
2024-10-27 09:25:45 DEBUG [CacheService] Cache invalidation triggered
2024-10-27 09:30:00 INFO [ReportGenerator] Monthly report generation started
```
10) Найти в файле logs.log строки, содержащие ERROR и вывести к какому сервису они относятся
11) Найти в файле logs.log строки, содержащие PaymentService и вывести из этих строк только email
12) Из вывода команды df -Th получить файловые системы с типом ext4
13) Из вывода команды free -h получить зачение столбца available
14) Из вывода команды lscpu получить значение Vendor ID
15) Выполнить команду apt list --installed и выяснить, установлен ли на машине python
16) Выполнить команду uptime и получить из ее вывода только значения load average
# Часть 2: Пользователи и права доступа
1) Создать группы: workers; teachers; students; вывести из файла /etc/group только названия добавленных групп
2) Создать пользователей user_{1,2,3,4,5}; вывести из файла /etc/passwd только имена созданных пользователей
3) Пользователей user_1 и user_2 добавить в группу workers
4) Пользователей user_3, user_4, user_5 добавить в группу students
5) Создать пользователя mentor3, задав ему при создании uid=3000, добавить в группу teachers
6) Вывести на экран состав групп workers; teachers; students
7) Задать пароли для всех пользователей
8) С помощью grep найти записи о новых группах и пользователях в файлах /etc/passwd и /etc/group
9) Создать директорию user в домашней директории. В ней создать каталоги library и tests.
10) Создать файлы book_фамилия_{1,2,3,4,5} и поместить их в library
11) Создать текстовый файл test_permissions, и поместить в tests; добавить в него следующий текст
```
#!/bin/bash
echo "Hello World"
```
12) Сделать файл test_permissions исполняемым для группы students
13) Переключиться на пользователя user_3 и запустить файл test_permissions
14) Дать право на изменение файла test_permissions только пользователю mentor3, а на чтение пользователям группы workers; проверить что это действительно сработало, переключаясь на пользователей
15) Создать пользователя test1, для которого запрещен вход в сеанс, имеющего домашний каталог /home/nouser и являющегося членом групп user и mail. Пользователь должен иметь UID равный 2000
16) Изменить имя пользователя test1 на test123.
17) Заблокировать пользователя test123
18) Создать группу пользователей xusers с GID, равным 1010
19) Изменить имя группы на yusers, а GID на 202
# Часть 3: Простая установка ПО
1) Установить на ВМ nginx, php, php-fpm, php-mysql и mariadb-server
2) Удалить apache2
3) Добавить установленные пакеты в автозагрузку
