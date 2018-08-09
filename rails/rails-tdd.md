## Installing RSPEC in rails project

1. Add these gems in Gemfile
```ruby
# development / test
group :development, :test do
  gem 'rspec-rails', '~> 3.6'
  gem 'capybara'
end
```

2. you must run this command:
```shell
docker-compose run web rails g rspec:install
```

3. Add **--format documentation** in ./.rspec file

4. Add spring-commands-rspec gem (it will optimize the speed of the tests)
```ruby
group :development do
  gem 'spring-commands-rspec'
end
```

5. Run this command:
```shell
docker-compose run web bundle exec spring binstub rspec
```

6. Add code in config/application.rb
```ruby
config.generators do  | g |
  g.test_framework :rspec,
    fixtures: false,
    view_specs: false,
    helper_specs: false,
    routing_specs: false
end
```

#### Finished.
Run: bin/rspec or rspec
```shell
docker-compose run web bin/rspec
```
