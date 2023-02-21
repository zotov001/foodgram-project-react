«Продуктовый помощник»: сайт, на котором пользователи публикуют рецепты, добавляют чужие рецепты в избранное и подписываются на публикации других авторов. Сервис «Список покупок» позволяет пользователям создавать список продуктов, которые нужно купить для приготовления выбранных блюд. 

admin@admin.ru
admin

Клонируйте репозиторий:

git clone git@github.com:zotov001/foodgram-project-react.git

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

После запуска:

Проект доступен по адресу: http://localhost/

Документация доступна по адресу: http://localhost/api/docs/

Автор сборки Марк zotov001@yandex.ru