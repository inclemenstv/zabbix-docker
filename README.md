# zabbix-docker

1. Первая возникшая проблема, заключеется в том что забикс-агент не доступен. Это потому-что по дефолту сервер ищет его на 127.0.01, а так как он у нас в другом контейнере нужно прописать ему ип-адрес контейнера!

Посмотреть ип адрес контейнера можно:
1. docker ps - смотрит ид нужного нам контейнера
2. docker inspect "id_conteiner" - покажет описание контейнера.
3. Далее изменим адрес в настройках хоста забикс сервера
![Screenshot_2](https://user-images.githubusercontent.com/19773509/116448397-c0827000-a861-11eb-9616-615d31ec96c2.jpg)
4. Сохраняем
5. Далее нужно выполнить команду на забикс сервере - zabbix_server -R config_cache_reload
Для этого нужно зайти в контейнер в интерактивном режиме:
docker exec -it "id_conteiner" /bin/bash или docker exec -it "id_conteiner" zabbix_server -R config_cache_reload

Полезные ссылки:
https://www.youtube.com/watch?v=ScKlF0ICVYA&t=957s
https://www.youtube.com/watch?v=PT_uqOpfHZU
https://gist.github.com/geraldvillorente/4c60e7fdb5562f443f16ad2bbe4235ce
https://www.zabbix.com/documentation/current/ru/manual/installation/containers
https://hub.docker.com/r/zabbix/zabbix-web-nginx-mysql
