# modbus

## Ruuun
1) откройте консоль и сокпируйте проект
```
git clone https://github.com/Revenan7/modbus.git
```
2) перейдите в директорию проекта:
```
cd modbus
```
3) выполните:
```
docker-compose up --build -d
```
у вас должен быть запущен докер*

## Использование
1) зайдите в CMD и зайдите в консоль контейнера:
```
docker exec -it modbus-modbus-client-1 /bin/bash
```
2) запустите файл
```
./start
```
для виртуального теста предоставлен modbus-server, доступный по IP: 172.19.0.2 PORT: 5020
его конфигурация в файле server.json


## Выгрузка данных
1) откройте консоль Git Bash и зайдите в директорию проекта
```
cd modbus
```
2) зайдите в терминал запущенного контейнера modbus-dbpostgres-1
```
docker exec -it modbus-dbpostgres-1 bash
```
3) выполните:
```
psql -U postgres -d postgres -c "Copy (Select * From responses) To STDOUT With CSV HEADER DELIMITER ',';" > db.csv
```
4) нажмите Ctrl + D или впишите exit, чтобы выйти из консоли контейнера

5) впишите
```
docker cp modbus-dbpostgres-1:/db.csv ./db.csv
```
