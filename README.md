# Devops assignment

This repository contains a simple api server written in laravel. 

## API Requirements
- PHP 8.2.22
- MySQL 8.0.39
- Redis 7.4

## Task 1
- Dockerize the application for production purposes.
- Create a docker compose yml file to run the application.
- Provide nginx configuration to serve the application.

**Note:** Commit messages should adhere to the Conventional Commits standard. Learn more about it here: https://www.conventionalcommits.org/en/v1.0.0/

### How to deploy?
Run following lines step-by-step

```bash
git clone https://github.com/Sajjadhz/devops-assignment.git
git checkout add-feature-dockerize
cd devops-assignment
cp .env.example .env
docker-compose up -d --build
docker-compose ps
docker-compose exec app ls -l
docker-compose exec app rm -rf vendor composer.lock
docker-compose exec app composer install
docker-compose exec app php artisan key:generate
docker-compose exec app touch /var/www/database/database.sqlite
docker-compose exec app chown goldab:goldab /var/www/database/database.sqlite
docker-compose exec app php artisan migrate
```

### To verify
Run following command, you should see corresponding expected output

```bash
curl -I localhost/up
```

Expected output:

```
HTTP/1.1 200 OK
Server: nginx/1.29.0
Content-Type: text/html; charset=UTF-8
Connection: keep-alive
X-Powered-By: PHP/8.2.29
Cache-Control: no-cache, private
Date: Sat, 19 Jul 2025 21:26:51 GMT
```