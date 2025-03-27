1) Запустить вторую ВМ с любым Linux
2) Настроить подключение по ssh между двумя ВМ без пароля (по ssh-ключам)
3) Изучить модули ansible
- setup
- debug
- package
- user
- file
- copy
4) Написать плейбук для получения информации о целевых хостах с помощью фактов. Собирать нужно следующие данные
- ip-адрес
- операционная система
- fqdn
- модель процессора
5) Написать плейбук по предварительной настройке целевых хостов. Необходимо
- установить пакеты 
```
bash-completion, git, curl, wget, ca-certificates, gnupg2, apt-transport-https, software-properties-common, zsh
```
- добавить пользователя admin с uid 5000, правами sudo и случайно сгенерированным паролем (можно сделать вывод пароля при прокатке чтобы потом проверить) и оболочкой zsh
6) Написать скрипт, который будет проверять свободное место на диске и написать плейбук по добавлению его на сервер и запуску с помощью cron
7) Написать плейбук golang-app. Плейбук должен
- установить на ВМ golang
- в директории /opt создать директорию server и положить туда файл server.go с содержимым
```
package main

import (
	"fmt"
	"os"
	"net/http"
)

var AppVersion = "1.0.0"

func funcHandler(w http.ResponseWriter, r *http.Request) {
	w.Write([]byte("Hello from DevOps in practice cource, app version is"+AppVersion))
}

func main() {
	Port := os.Getenv("PORT")
	if Port == "" {
		Port = "3000"
	}
	fmt.Print("\nApp version", AppVersion, "running on", Port)
	mux := http.NewServeMux()
	mux.HandleFunc("/", funcHandler)
	http.ListenAndServe(":"+Port, mux)
}
```
- собрать код с помощью команды
```
CGO_ENABLED=0 GO111MODULE=off GOOS=linux go build -o server server.go
```
- запустить server как systemd сервис __!!(юнит-файл написать самостоятельно)!!__
