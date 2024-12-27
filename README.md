# modbus

## Ruuun
откройте консоль и сокпируйте проект
```bash
git clone https://github.com/Revenan7/modbus.git
```

## Использование
1) зайдите в CMD и зайдите в консоль контейнера:
```
docker exec -it modbus-modbus-client-1 /bin/bash
```
2) запустите файл
```
./start
```


## Выгрузка данных
1) откройте консоль Git Bash и зайдите в директорию проекта
```
cd modbus
```
2) выполните:
```
docker-compose up --build -d
```
3) зайдите в терминал запущенного контейнера modbus-dbpostgres-1
```
docker exec -it modbus-dbpostgres-1 bash
```
4) выполните:
```
psql -U postgres -d postgres -c "Copy (Select * From responses) To STDOUT With CSV HEADER DELIMITER ',';" > db.csv
```
5) нажмите Ctrl + D или впишите exit, чтобы выйти из консоли контейнера

6) впишите
```
docker cp modbus-dbpostgres-1:/db.csv ./db.csv
```
