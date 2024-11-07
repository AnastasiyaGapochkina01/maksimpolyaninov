# Часть 1
1) Установить на ВМ php, если еще не установлен
2) В директории /opt создать папку rot13
3) В директории /opt/rot13 создать файл с именем rot13-server.php с кодом
```
<?php
$sock = socket_create(AF_INET, SOCK_DGRAM, SOL_UDP);
socket_bind($sock, '0.0.0.0', 10000);
for (;;) {
  socket_recvfrom($sock, $message, 1024, 0, $ip, $port);
  $reply = str_rot13($message);
  socket_sendto($sock, $reply, strlen($reply), 0, $ip, $port);
}
```
4) Запустить сервер командой php rot13-server.php и проверить что сервер работает: выполнить nc -u 127.0.0.1 10000 и ввести Hello World
5) Написать юнит-файл для запуска rot13-server.php как сервиса
# Часть 2
1) Написать юнит-файл для запуска [скрипта](https://gist.github.com/AnastasiyaGapochkina01/8e77f63f288139e5ddd87b105d1e3c12) как сервиса systemd, создать таймер для периодического выполнения задачи
про таймеры можно посмотреть тут https://youtu.be/hTkaCE5Mz8I

если сервис хотя бы раз удачно отработал, то должен появиться файл /var/log/dsk-usage.log с записью примерно такого вида
```
1730956510 [ALARM] Disk usage for / is greater then 5: current value is 35
```
2) Написать юнит-файл для запуска простого [веб-сервера на python](https://gist.github.com/AnastasiyaGapochkina01/ac33a8174326f80a1af1ed9f4754541e). После того как сервис запустится выполнить команду
```
curl 127.0.0.1:9999
```
ответ должен быть _Hello from Python_
# Часть 3 (задача со звездочкой)
1) Установить redis ([install-redis-on-linux](https://redis.io/docs/latest/operate/oss_and_stack/install/install-redis/install-redis-on-linux/))
2) Посмотреть статус демона redis
3) Запустить второй экземпляр демона redis, написав systemd unit
