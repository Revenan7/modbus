# modbus

## Ruuun
1) откройте консоль Git Bash и скопируйте репозиторий в папку
```bash
git clone https://github.com/Revenan7/modbus.git
```
2) зайдите в директорию проекта
```
cd modbus
```
3) выполните:
```
docker-compose up --build -d
```
4) зайдите в терминал запущенного контейнера modbus-dbpostgres-1
```
docker exec -it modbus-dbpostgres-1 bash
```
5) выполните:
```
psql -U postgres -d postgres -c "Copy (Select * From responses) To STDOUT With CSV HEADER DELIMITER ',';" > db.csv
```
6) нажмите Ctrl + D или впишите exit, чтобы выйти из консоли контейнера

7) впишите
```
docker cp modbus-dbpostgres-1:/db.csv ./db.csv
```
