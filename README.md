u12rubpls
================

Shippable CI image for Ruby on Ubuntu 12.04 with commonly used services. Available versions are:

1. 1.8.7
2. 1.9.3
3. 2.0.0
4. 2.1.5
5. 2.2.1

Services
1. elasticsearch 1.5
2. memcached 1.4
3. mongodb 3.0
4. mysql 5.6
5. postgres 9.4
6. rabbitmq 3.5
7. redis 3.0
8. selenium 2.45
9. sqllite 3

## How to use
You can use this image to run ruby builds on Shippable. Just update your
`shippable.yml` file and add the `build_image` directive. You should also
activate the appropriate rvm so your build runs against the
correct version of ruby. You can use `$SHIPPABLE_RUBY` environment variable to specify ruby versions. Here's a sample YML file to get you going:

````

language: ruby
build_image: drydock/u12rubpls:prod

rvm:
  - 1.8.7
  - 1.9.3
  - 2.0.0
  - 2.1.5
  - 2.2.1

services:
  - elasticsearch
  - memcached
  - mongodb
  - mysql
  - postgres
  - rabbitmq
  - redis
  - selenium
  - sqllite

before_install:
 - source ~/.rvm/scripts/rvm
 - rvm install $SHIPPABLE_RUBY --verify-downloads 1
 - source ~/.bashrc && ~/.rvm/scripts/rvm && rvm use $SHIPPABLE_RUBY
 
install:
 - bundle install --gemfile="Gemfile"
 - ruby -v

script:
- bundle exec rake

````
