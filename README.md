# docker-rails

## setup development

```
# setup docker
$ git clone https://github.com/inocop/docker-rails.git
$ cd docker-rails/docker/app_dev/
$ docker-compose up -d --build

# setup rails
$ docker-compose exec app bash
[docker]$ gem install --no-document rails
[docker]$ cd /var/www/app/source
[docker]$ rails _5.2.2_ new . --database=mysql --skip-bundle --skip-coffee --skip-turbolinks --skip-sprockets
[docker]$ bunlde install
```
