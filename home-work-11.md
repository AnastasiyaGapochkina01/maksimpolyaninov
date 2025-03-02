1) Написать Dockerfile для запуска приложения https://github.com/AnastasiyaGapochkina01/sample-ruby-app. Запустить из собранного образа контейнер и проверить работу:\
```curl 127.0.0.1:3000``` должен отдавать "Hello, world!"
2) Написать Dockerfile для компиляции и запуска программы на c
```
#include <stdio.h>
#include <time.h>
#include <unistd.h>

int main() {
    char hostname[1024];
    gethostname(hostname, 1024);

    time_t rawtime;
    struct tm * timeinfo;
    time(&rawtime);
    timeinfo = localtime(&rawtime);

    printf("%04d-%02d-%02d %02d:%02d:%02d running on %s\n",
           timeinfo->tm_year + 1900, // Год
           timeinfo->tm_mon + 1,     // Месяц
           timeinfo->tm_mday,        // День
           timeinfo->tm_hour,        // Час
           timeinfo->tm_min,         // Минута
           timeinfo->tm_sec,         // Секунда
           hostname);

    return 0;
}
```
для запуска программы как фонового процесса можно использовать entrypoint.sh
```
#!/usr/bin/env bash

while true; do
  /app/hostname
  sleep 1
done
```
где /app/hostname - скомпилированный бинарный файл программы
Запустить из собранного образа контейнер и проверить работу:\
- ```docker logs container-id``` должна отдавать похожий ответ
```
2025-03-02 05:24:17 running on 1e6c8aa77038
2025-03-02 05:24:18 running on 1e6c8aa77038
2025-03-02 05:24:19 running on 1e6c8aa77038
```
3) Написать Dockerfile для создания кастомного php-fpm. За основу взять php:8.2-fpm. Включить модули
- intl
- gd
- ldap
- pdo_mysql
- soap zip
```
;The maximum size of an uploaded file.
upload_max_filesize = 50M

;Sets max size of post data allowed. This setting also affects file upload. To upload large files, this value must be larger than upload_max_filesize
post_max_size = 70M
max_input_vars = 10000

#opcache.validate_timestamps=1
opcache.revalidate_path = On
```
