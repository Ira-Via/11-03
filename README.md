# 11-03  
11-03 «ELK» Васяева Ирина  
# Задание 1  
1. Скачивание и установка.  
![image](https://github.com/user-attachments/assets/9fd337ce-eb39-4b88-b74e-7a9ae49dd172)   
![image](https://github.com/user-attachments/assets/9d264260-472c-47fa-a671-2ccdad92c300)   
```  
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.17.0-linux-x86_64.tar.gz  
   tar -xzf elasticsearch-8.17.0-linux-x86_64.tar.gz
   cd elasticsearch-8.17.0
```
2. Запуск.  
`./bin/elasticsearch`  
3. Изменение параметра   
![image](https://github.com/user-attachments/assets/d38577c1-6021-403d-8f05-3c2851697d0c)  
4. Сохранение и перезапуск кластера:  
```
./bin/elasticsearch-stop
./bin/elasticsearch
```
5. Проверка кластера:  
`curl -X GET 'localhost:9200/_cluster/health?pretty'`
6. Результат:  
```
{
  "cluster_name" : "my_random_cluster",
  "status" : "yellow",
  "timed_out" : false,
  "number_of_nodes" : 1,
  "number_of_data_nodes" : 1,
  ...
}
```
# Задание 2.  
1. Скачивание и установка:   
```
 wget https://artifacts.elastic.co/downloads/kibana/kibana-8.2.2-linux-x86_64.tar.gz
   tar -xzf kibana-8.2.2-linux-x86_64.tar.gz
   cd kibana-8.2.2
```
2. Настройка конфигурации:   
![image](https://github.com/user-attachments/assets/35ca1f96-01e7-44e2-9425-fa40491e1502)  
3. Запуск:  
`./bin/kibana`
4. Выполнение запроса:  
` GET /_cluster/health?pretty`
# Задача 3.  
1. Установка Nginx  
![image](https://github.com/user-attachments/assets/7281b2d5-1ba5-41be-b908-960523885612)  
2. Установка Logstash  
```
wget https://artifacts.elastic.co/downloads/logstash/logstash-8.17.0.deb
sudo dpkg -i logstash-8.17.0.deb
```
3. Запись конфигурации для обработки логов  
![image](https://github.com/user-attachments/assets/10ee9c89-b484-493c-9678-f1ed5c584787)  
4. Запуск Logstash  
`sudo systemctl start logstash`  
5. Запуск Kibana:   
`./bin/kibana`  
6. Создание индекс:  
В Kibana открываем раздел "Management" -> "Index Patterns" и создаем новый индекс с именем nginx-logs-*.  
7. Проверка логи:  
Переход в "Discover" и выбор созданного индекса, чтобы увидеть свои Nginx логи.  
# Задание 4  
1. Установка Filebeat:  
```
wget https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-8.17.0-amd64.deb
   sudo dpkg -i filebeat-8.17.0-amd64.deb
```
2. Настройка Filebeat для Nginx:  
![image](https://github.com/user-attachments/assets/c7af0b87-7a47-459d-9be2-d52d6d01a9e2)  
![image](https://github.com/user-attachments/assets/d949f5d3-81fc-428f-9394-99c3359e87e2)
3. Запуск Filebeat
```
sudo systemctl start filebeat
sudo systemctl enable filebeat
```
4. Проверка логов в Kibana
