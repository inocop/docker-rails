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
[docker]$ rails _5.2.2_ new . --database=mysql --skip-bundle --skip-coffee --skip-turbolinks --skip-sprockets --skip-spring
[docker]$ bundle install

# edit config
#
# config/application.rb
#   module Source -> module MyApp
#
# config/database.yml
#   password: root
#       host: localhost -> db
#   database: source_development -> myapp_dev

# create database
[docker]$ bundle exec rake db:create

# restart rails
[docker]$ supervisorctl restart rails
```
