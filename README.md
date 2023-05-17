# README
This is a way to set up SSL fast for localhost in a Ruby on Rails 7 app.

The first command is required. Running the server is optional if you don't include the change to the config/puma.rb file. With the change to the puma file, you can just run a `rails s` and visit the port in your puma file (Defaulted to 3001) to see your https app. EX: By default it's set to 3001 in the puma file, so visiting https://localhost:3001 will be how you can use SSL.

## Create SSL Cert
```sh
openssl req -x509 -sha256 -nodes -newkey rsa:2048 -keyout localhost.key -out localhost.crt -subj "/CN=localhost" -days 365
```
## Run Server

```sh
rails s -b "ssl://localhost:3000?key=config/ssl/localhost.key&cert=config/ssl/localhost.crt"
```