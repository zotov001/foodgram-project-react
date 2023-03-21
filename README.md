Foodgram - «Продуктовый помощник»
Сервис, на котором пользователи публикуют рецепты, добавляют чужие рецепты в избранное и подписываются на публикации других авторов. «Список покупок» позволяет пользователям создать и скачать список продуктов, которые нужно купить для приготовления выбранных блюд (суммарно). 

Технологии:

Python, Django, Django Rest Framework, Docker, Gunicorn, NGINX, PostgreSQL, Yandex Cloud, Continuous Integration, Continuous Deployment


Для развертывания проекта локально:

Клонируйте репозиторий:

git clone git@github.com:zotov001/foodgram-project-react.git

Создайте файл .env в каталоге с settings.py:

    SECRET_KEY=<секретный ключ проекта django>
    DB_ENGINE=<django.db.backends.postgresql>
    DB_NAME=<имя базы данных postgres>
    DB_USER=<пользователь бд>
    DB_PASSWORD=<пароль>
    DB_HOST=<db>
    DB_PORT=<5432>
    

Установите docker:

sudo apt install docker.io

Установите docker-compose:

sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose

Собираем контейнерыы:

Из папки infra/ разверните контейнеры при помощи docker-compose:

docker-compose up -d --build

Выполните миграции:

docker-compose exec backend python manage.py migrate

Создайте суперпользователя:

docker-compose exec backend python manage.py createsuperuser

Соберите статику:

docker-compose exec backend python manage.py collectstatic --no-input

Наполните базу данных ингредиентами.

docker-compose exec backend python manage.py load_ingredients

Остановка проекта:

docker-compose down

Для работы с Workflow добавьте в Secrets GitHub переменные окружения:

    DB_ENGINE=<django.db.backends.postgresql>
    DB_NAME=<имя базы данных postgres>
    DB_USER=<пользователь бд>
    DB_PASSWORD=<пароль>
    DB_HOST=<db>
    DB_PORT=<5432>
    DOCKER_PASSWORD=<пароль от DockerHub>
    DOCKER_USERNAME=<имя пользователя>
    SECRET_KEY=<секретный ключ проекта django>
    USER=<username для подключения к серверу>
    HOST=<IP сервера>
    PASSPHRASE=<пароль для сервера, если он установлен>
    SSH_KEY=<ваш SSH ключ (для получения команда: cat ~/.ssh/id_rsa)>
    TELEGRAM_TO=<ID чата, в который придет сообщение>
    TELEGRAM_TOKEN=<токен вашего бота>
    
Workflow состоит из трёх шагов:
Проверка кода на соответствие требованиям PEP8;
Сборка и публикация образа на DockerHub;
Автоматический деплой на удаленный сервер;
Отправка уведомления в телеграм-чат;

Автор сборки Марк zotov001@yandex.ru
