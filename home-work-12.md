1) Запустить с помощью docker compose gitea (https://hub.docker.com/r/gitea/gitea) и postgres
- gitea - аналог gitlab. Потребуются переменные
```
DB_TYPE=postgres
DB_HOST=db:5432
DB_NAME=gitea
DB_USER=gitea
DB_PASSWD=gitea
``` 
2) Запустить с помощью docker compose prometheus и grafana
3) Запустить wordpress с помощью docker compose
4) Запустить с помощью docker compose mongodb и mongo-express (админка к монге https://hub.docker.com/_/mongo-express)
5) С помощью docker compose запустить matomo (https://hub.docker.com/r/bitnami/matomo)
6) Запустить с помощью docker compose приложения из репозитория https://github.com/AnastasiyaGapochkina01/compose-apps/tree/main
