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

## 2. edit .envtest file
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

## 3. build&up the container
Use commands
> docker compose build <br>
> docker compose up -d<br>

## 4. apply migrations&load fixtures
### 4.1 aplly migrations
> docker-compose exec web python manage.py migrate

### 4.2 load fixtures (IN ORDER BELOW!)
> docker-compose exec web python manage.py loaddata products_product_category_202603130004_django.json
> docker-compose exec web python manage.py loaddata users_user_202603130004_django_fixed.json
> docker-compose exec web python manage.py loaddata products_product_202603130004_django.json
> docker-compose exec web python manage.py loaddata products_order_202603130004_django.json
> docker-compose exec web python manage.py loaddata products_basket_202603130004_django.json<br>

### 5. visit localhost:8080
Enjoy django-shop site!

