1) Написать Dockerfile для запуска в docker кода на php
```
<?php
phpinfo();
?>
```

> [!NOTE]  
> В качестве базового image можно взять php:8.0-apache. 

Запустить из собранного image контейнер и проверить его работоспособность

2) Написать Dockerfile для приложения https://github.com/AnastasiyaGapochkina01/node-app, запустить из собранного image контейнер и проверить его работоспособность
3) Написать Dockerfile для приложения https://github.com/hackersandslackers/golang-helloworld, запустить из собранного image контейнер и проверить его работоспособность (```curl 127.0.0.1:9100```)
4) Написать Dockerfile для приложения https://github.com/AnastasiyaGapochkina01/flask-poetry/tree/main, запустить из собранного image контейнер и проверить его работоспособность (```curl 127.0.0.1:5000```)
5) Написать Dockerfile для собственной версии nginx:
- удалить конфиг по умолчанию (default)
- создать конфиг файл для статического сайта, расположенного в /var/www/landing
- установить в image:
  - vim
  - iputils-ping
  - iproute2
  - dnsutils
- установить таймзону Europe/Moscow
- изменить пользователя в главном конифге nginx на www-data
- в директорию /etc/nginx положить файл deny.conf
```
location ~ /\.ht {
    return 404;
}
location ~ /\.svn {
    return 404;
}
location ~ /\.git {
    return 404;
}
location ~ /web.config {
    return 404;
}
```
- в директорию /var/www/landing положить файлы из репозитория https://github.com/AnastasiyaGapochkina01/book-landing/tree/main/book

Запустить из собранного image контейнер и проверить его работоспособность - при запросе должен отдаваться похожий на это https://themes.3rdwavemedia.com/demo/bs5/devbook/ лендинг
