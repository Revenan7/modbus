# modbus

Совместная работа с https://github.com/kreipikc

## Ruuun
1) откройте CMD и скопируйте проект
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
4) убедитесь, что контейнер с ьазой данных собрался и запустился:

![image](https://github.com/user-attachments/assets/7392f97a-0499-4af1-9c96-774377b4b43e)


у вас должен быть запущен докер*

## Использование
1) разархивируйте архив:

![image](https://github.com/user-attachments/assets/ccb46992-538f-4c85-8ca0-543ee3c7e621)


2) запустите файл

![image](https://github.com/user-attachments/assets/b33a0173-49e3-45e1-9c12-af8e6045b92e)



## про команды
![image](https://github.com/user-attachments/assets/f4e90ced-3507-43fe-be63-04ac29320c6c)
## 1) создание новой команды
   
![image](https://github.com/user-attachments/assets/4c27ed6c-36de-4183-91be-bb02f6a01add)

первая цифра - код фунцкии
```
1 - Read Coil Status

2 - Read Input Status

3 - Read Holding Registers

4 - Read Input Registers
```
вторая цифра - с какого регистра считывать

третья цифра - сколько регистров считывать

пример:

4 9 1

программа создаст функцию, которая считывает Input Register по адресу 9

## 2) запуск команды по ID

  а) введите IP адрес устройства, доступный в локальной сети
  
  б) введите порт этого устройства
  
  в) введите номер команды (доступные команды, которые вы создали можно посмотреть)
  
  если всё прошло успешно:
  
 ![image](https://github.com/user-attachments/assets/8046a679-d66f-4f52-aadf-5ed9898619e9)

  
  (данная функция, прочла Input Register по адрессу 9, в устройстве доступный по IP 127.0.0.1 и порту 502)

## 3) вывод всех доступных команд (которые вы создали ранее)
пример:

![image](https://github.com/user-attachments/assets/f2847aef-06d4-4c9c-b97e-3291c66d15ef)


## 4) вывод логов, всех отправленных пакетов и принятых соответсвенно
пример:

![image](https://github.com/user-attachments/assets/d3923b77-345c-4fa7-921a-04ee5b65b1ca)


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

в папке проекта создастся файл

![image](https://github.com/user-attachments/assets/28b18f63-c835-43fc-a007-8df2ffd11289)

