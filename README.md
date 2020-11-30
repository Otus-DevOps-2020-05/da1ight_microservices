# da1ight_microservices
da1ight microservices repository

Домашнее задание №11
* Установлен docker, docker-compose, docker-machine
* Созданы \
 1 Dockerfile - текстовое описание нашего образа \
 2 mongod.conf - подготовленный конфиг для mongodb \
 3 db_config - содержит переменную окружения со ссылкой на mongodb \
 4 start.sh
* Создам имидж приложения reddit
* Запущен контейнер с приложение reddit
* Имидж запушен в docker-hub
* Создана VM с помощью yc и через docker-machine инициализирована на нём докер хост систему

Задание со *
Разница между контейнером и имиджем описана в файле dockermonolith/docker-1.log

Домашнее задание №12
* Научились описывать и собирать Docker-образы для сервисного приложения
* Научились оптимизировать работу с Docker-образами
* Запустили приложения на основе Docker-образов, оценка удобства запуска контейнеров при помощи docker run
* Разбили наше приложение на несколько компонентов

Задание со * \
Необходимо перезапустить контейнеры и передать через `-e` следующие переменные: \
POST_DATABASE_HOST \
COMMENT_DATABASE_HOST \
POST_SERVICE_HOST \
COMMENT_SERVICE_HOST \

Задание со * 2 \
Имиджи comment и ui перенесены на базовый образ alpine. 
Созданы Dockerfile_ в папках соответсвенно микросервису

```
$ docker images
REPOSITORY            TAG                 IMAGE ID            CREATED             SIZE
da1ight/ui            777                 9bf8bfe74cc1        7 minutes ago       74.7MB
da1ight/comment       777                 80c71948eed3        9 minutes ago       72.6MB
da1ight/ui            2.0                 75355409d749        5 hours ago         457MB
da1ight/ui            1.0                 2647a47c0c2b        5 hours ago         771MB
da1ight/comment       1.0                 50d961efd670        5 hours ago         768MB
da1ight/post          1.0                 81cf93e3ff34        5 hours ago         110MB
mongo                 latest              ef5c2207766e        4 days ago          493MB
```
