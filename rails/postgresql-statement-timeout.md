# Setting statement_timeout in Rails and Postgresql

You can set a default statement_timeout across all PostgreSQL connections in your Rails app. It helps prevent long queries or migrations from bringing down production.


```yml
default: &default
  adapter: postgresql
  encoding: unicode
  pool: <%= ENV.fetch("RAILS_MAX_THREADS", "3") %>
  min_messages: warning
  # connection timeout
  timeout: 5000
  variables:
    statement_timeout: "30s"
```
