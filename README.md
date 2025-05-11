# Disaster recovery и Keepalived `Щербатых А.Е.`
## Задание 1
1. Дана схема для Cisco Packet Tracer, рассматриваемая в лекции.
2. На данной схеме уже настроено отслеживание интерфейсов маршрутизаторов Gi0/1 (для нулевой группы)
3. Необходимо аналогично настроить отслеживание состояния интерфейсов Gi0/0 (для первой группы).
4. Для проверки корректности настройки, разорвите один из кабелей между одним из маршрутизаторов и Switch0 и запустите ping между PC0 и Server0.
5. На проверку отправьте получившуюся схему в формате pkt и скриншот, где виден процесс настройки маршрутизатора.

### Решение

схема
[hsrp_advanced_HW_10_1.pkt](images/hsrp_advanced_HW_10_1.pkt)

Настройка роутеров и проверка пинга

 ![alt text](https://github.com/Anton-Shcherbatykh/FOPS-32_6/blob/main/images/%D0%97%D0%B0%D0%B4%D0%B0%D0%BD%D0%B8%D0%B5%201.jpg)

  ![alt text](https://github.com/Anton-Shcherbatykh/FOPS-32_6/blob/main/images/%D0%97%D0%B0%D0%B4%D0%B0%D0%BD%D0%B8%D0%B5%201_1.jpg)
  

## Задание 2
1. Запустите две виртуальные машины Linux, установите и настройте сервис Keepalived как в лекции, используя пример конфигурационного файла.
2. Настройте любой веб-сервер (например, nginx или simple python server) на двух виртуальных машинах
3. Напишите Bash-скрипт, который будет проверять доступность порта данного веб-сервера и существование файла index.html в root-директории данного веб-сервера.
   
   скрипт [HW_10_1_chek_server.sh](https://github.com/Anton-Shcherbatykh/FOPS-32_6/blob/main/images/HW_10_1_chek_server.sh)
4. Настройте Keepalived так, чтобы он запускал данный скрипт каждые 3 секунды и переносил виртуальный IP на другой сервер, если bash-скрипт завершался с кодом, отличным от нуля (то есть порт веб-сервера был недоступен или отсутствовал index.html). Используйте для этого секцию vrrp_script
   
   Демонстрация переезда плавающего ip на другой сервер в случае недоступности порта:
   Порт доступен
    ![alt text](https://github.com/Anton-Shcherbatykh/FOPS-32_6/blob/main/images/%D0%97%D0%B0%D0%B4%D0%B0%D0%BD%D0%B8%D0%B5_2_5.jpg)
    ![alt text](https://github.com/Anton-Shcherbatykh/FOPS-32_6/blob/main/images/%D0%97%D0%B0%D0%B4%D0%B0%D0%BD%D0%B8%D0%B5_2_6.jpg)

   Порт недоступен
    ![alt text](https://github.com/Anton-Shcherbatykh/FOPS-32_6/blob/main/images/%D0%97%D0%B0%D0%B4%D0%B0%D0%BD%D0%B8%D0%B5_2_7.jpg)
    ![alt text](https://github.com/Anton-Shcherbatykh/FOPS-32_6/blob/main/images/%D0%97%D0%B0%D0%B4%D0%B0%D0%BD%D0%B8%D0%B5_2_8.jpg)
   файл конфигурации тут [keepalived.conf](https://github.com/Anton-Shcherbatykh/FOPS-32_6/blob/main/images/keepalived.conf)

   ### прошу помочь разобраться, почему скрипт не запускается для пользователя keepalived_script
6. На проверку отправьте получившейся bash-скрипт и конфигурационный файл keepalived, а также скриншот с демонстрацией переезда плавающего ip на другой сервер в случае недоступности порта или файла index.html
