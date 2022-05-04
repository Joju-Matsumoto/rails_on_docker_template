# Rails7 (postgresql) on Docker

## Usage
1. confirm Dockerfile, docker-compose.yml
1. `docker-compose run --no-deps web rails new . --force --database=postgresql --skip-bundle`
1. `docker-compose build`
1. edit `config/database.yml`
```yaml=
default: &default
  adapter: postgresql
  encoding: unicode
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  host: db              # db service name
  username: postgres    # root
  password: password    # POSTGRES_PASSWORD

development:
  <<: *default
  database: myapp_development

test:
  <<: *default
  database: myapp_test
```
1. `docker-compose run web rails db:create`
1. `docker-compose up`