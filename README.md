# version 1.0.0 (just backend)
Contains default logic for django-online-shop, such as:
- users
- products
- cart
- orders <br>

# technologies
- python
- django
- django orm
- postgresql
- docker/docker-compose

# deploy
## 1. clone this .git repo
Use
> git clone https://github.com/FLEMMINDO/django-shop.git

## 2. create postgresql database
Use pgadmin4 or psql (save credentials)

## 3. edit .envtest file
Switch filename into
> .envtest -> .env

Edit .env file, put values into
### NECESSARY FOR BUILD:

- DB_HOST=*localhost* __OR__ *your value*
- DB_PORT=*5432* __OR__ *your value*
- DB_USER=*postgres* __OR__ *your value*
- DB_PASSWORD=*password12345* __OR__ *your value*
- DB_NAME=*django_shop_prod* __OR__ *your value*<br>

- SECRET_KEY=*your value* # generate with python -c "from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())"<br>

## 4. build&up the container
Use commands
> docker compose build <br>
> docker compose up -d<br>

## 5. apply migrations&load fixtures
### 5.1 aplly migrations
> docker-compose exec web python manage.py migrate

### 5.2 load fixtures (IN ORDER BELOW!)
> docker-compose exec web python manage.py loaddata products_product_category_202603130004_django.json<br>
> docker-compose exec web python manage.py loaddata users_user_202603130004_django_fixed.json<br>
> docker-compose exec web python manage.py loaddata products_product_202603130004_django.json<br>
> docker-compose exec web python manage.py loaddata products_order_202603130004_django.json<br>
> docker-compose exec web python manage.py loaddata products_basket_202603130004_django.json<br>

### 6. visit localhost:8080
Enjoy django-shop site!

