## Creating a new Rails application project with Docker

### 10 STEPS
1. Create a file `Dockerfile`
2. Create a folder `app/`
It's will be used for your application rails
3. Create a `Gemfile` inside app folder
```ruby
# Gemfile Content
source 'https://rubygems.org
gem 'rails', '5.1.4'
```
4. Create a Gemfile.lock inside app folder
5. Create a new application rails
```shell
docker-compose run web rails new . -d postgresql
```
6. Now, It needs build to run bundle install
```shell
docker-compose build
```
7. Runs rails server
```shell
docker-compose up -d
```
8. Configure rails DB. Adding some informations of database server

**If you are running Docker on Linux, change the ownership of the new files:**
```shell
sudo chown -R $USER:$USER .
```

9. Update this file config/database.yml
```yml
default: &default
  adapter: postgresql
  encoding: unicode
  host: dbpg
  username: pguser
  password: 
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>

development:
  <<: *default
  database: app_development

test:
  <<: *default
  database: app_test

# production:
#   <<: *default
#   database: app_production
#   username: app
#   password: <%= ENV['APP_DATABASE_PASSWORD'] %>
```

10. Generate database on rails
```shell
docker-compose run web rails db:create
```
