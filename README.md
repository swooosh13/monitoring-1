# Перед началом
1. docker compose up -d
2. задать пароль для expoter user mariadb (взять пароль для root в .env/${MYSQL_ROOT_PASSWORD}):

```
mysql> CREATE USER 'exporter'@'%' IDENTIFIED BY 'exporterpassword' WITH MAX_USER_CONNECTIONS 3;
mysql> GRANT PROCESS, REPLICATION CLIENT, SELECT ON *.* TO 'exporter'@'%';
```

3. установить плагин в wordpress

3.1. скачать архив

`https://github.com/origama/wordpress-exporter-prometheus`

3.2.
установить плагин на localhost:80 -> Плагины -> Добавить плагин -> импортировать архив / папку



4. docker compose restart

### Структура проекта
- le/         - файлы сертов для letsencrypt.
- nginx/      - конфиг для nginx.
- wp-content/ - wordpress volume.
- docker-compose.yml - настройки кластера
