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

Домашнее задание №13

* Протестирована работа в сети docker none, host, bridge
* Запущены микросервисы проекта с использованием сети bridge c использованием сетевых алиасов: указываем --network-alias при старте контейнеров
* Протестирован запуск проекта в 2-х bridge сетях: back_net и front_net
для корректной работы приложения контейнеры post и comment были помещены в обе сети. Иначе контейнеры из соседних сетей не будут доступны как в DNS, так и для взаимодействия по сети.
* Изучен сетевой стек Linux при работе микросервисов с использованием сети bridge
* Реализован запуск проекта с использованием docker-compose:
создан файл docker-compose.yml, файл переменных .env (env_file=.env в docker-compose.yml), возможно запускать с опцией `--env-file reddit.env` \
* Параметризованы: 
    1. username
    2. порт публикации сервиса ui
    3. версии имиджей
* Чтобы docker-compose сущности имели в качестве префикса имя проекта мы можем запустить его с опцией `docker-compose --project-name reddit up -d` \
Так же я добавил переменную COMPOSE_PROJECT_NAME=reddit в файл параметров. По умолчанию будет использоваться название каталога проекта в качестве префикса

Задание со (**) \
Создан файл docker-compose.override.yml, позволяющий запускать puma для руби приложений в дебаг режиме с двумя воркерами (флаги --debug и -w 2)

Домашнее задание №14

Cоздана YC-виртуальная машина gitlab-ci-vm с помощью web консоли
Установлен docker-compose на ВМ через docker-machine \
```docker-machine create --driver generic --generic-ip-address=130.193.35.37 --generic-ssh-user ubuntu --generic-ssh-key ~/.ssh/keys/yc gitlab-ci``` \
Запущен gitlab в docker-контейнере, запущен контейнер с gitlub-runner и регистрируем его. 
Описаны этапы пайплайна для приложения 
Определены окружения