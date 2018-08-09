## Add these gems in Gemfile

```ruby
# development / test
group :development, :test do
  gem 'rspec-rails', '~> 3.6'
  gem 'capybara'
end
```

After that, you must run this command:
```shell
docker-compose run web rails g rspec:install
```
