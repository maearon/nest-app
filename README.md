# RESTful API Nest Server 🇻🇳

## Description

[Nest](https://github.com/nestjs/nest) framework TypeScript starter repository.

## Installation

```bash
$ npm i -g npm-check-updates
$ ncu -u
$ npm install
$ cp env-example .env
```

## Running the app

```bash
# development
$ npm run start

# watch mode
$ npm run start:dev

# production mode
$ npm run start:prod

# docker
$ docker container kill $(docker container ls -q)
$ docker-compose up --build
$ docker-compose exec api bash
$ npm run migration:run
$ npm run seed:run
$ docker exec -it nest-app_postgres_1 bash
api-# psql -U root -W api
api-# Password: secret
$ docker exec -it nest-app_postgres_1 psql -U root -W api
api-# \dt
          List of relations
 Schema |    Name    | Type  | Owner 
--------+------------+-------+-------
 public | file       | table | root
 public | forgot     | table | root
 public | migrations | table | root
 public | role       | table | root
 public | status     | table | root
 public | user       | table | root
(6 rows)
```

## Project Structure

```
src\
 |--\src\config\                                          # Environment variables and configuration related things
 |--\src\...\...controller.ts                             # Route controllers (controller layer)
 |--src\...\entites\                                      # Swagger files
 |--(middlewares)\                                        # Custom nest middlewares
 |--\src\models\users\                                    # Postgres models (data layer)
 |--\src\...\...controller.ts(routes)\                    # Routes
 |--\src\auth-database-files-forgot-mail-users(services)\ # Business logic (service layer)
 |--\src\utils\                                           # Utility classes and functions
 |--\src\utils\validators\                                # Request data validation schemas
 |--\src\app.module.ts                                    # Nest app
 |--\src\main.js                                          # App entry point
```

## API Documentation

To view the list of available APIs and their specifications, run the server and go to `http://localhost:3000/docs` in your browser. This documentation page is automatically generated using the [swagger](https://swagger.io/) definitions written as comments in the route files.
https://editor.swagger.io/ coppy from swagger.yaml
MailDev using directory `/tmp/maildev-8`
MailDev webapp running at `http://0.0.0.0:1080`
MailDev SMTP Server running at `0.0.0.0:1025`
Database Adminer `http://localhost:8080/`

## API Endpoints

List of available routes:

**Auth routes**:\
`POST /api/v1/auth/email/register` - register\
`POST /api/v1/auth/admin/email/login` - login\
`POST /api/v1/auth/email/logout` 
`POST /api/v1/auth/email/refresh` - refresh auth tokens\
`POST /api/v1/auth/forgot/password` - send reset password email\
`POST /api/v1/auth/reset/password` - reset password\
`POST /api/v1/auth/email/verification` - send verification email\
`POST /api/v1/auth/email/confirm` - verify email
`GET /api/v1/auth/me`
`PATCH /api/v1/auth/me`
`DELETE /api/v1/auth/me` - logout\
`POST /api/v1/auth/facebook/login`
`POST /api/v1/auth/google/login`
`POST /api/v1/auth/twitter/login`
`POST /api/v1/auth/apple/login`

**User routes**:\
`POST /api/v1/users` - create a user\
`GET /api/v1/users` - get all users\
`GET /api/v1/users/:id` - get user\
`PATCH /api/v1/users/:id` - update user\
`DELETE /api/v1/users/:id` - delete user

**Files routes**:\
`POST /api/v1/files/upload` - upload file\
`GET /api/v1/users/:path` - get file\

## Test

```bash
# unit tests
$ npm run test

# e2e tests
$ npm run test:e2e

# test coverage
$ npm run test:cov

# test in docker
$ docker compose -f docker-compose.ci.yaml --env-file env-example -p ci up --build --exit-code-from api && docker compose -p ci rm -svf
$ docker run --rm jordi/ab -n 100 -c 100 -T application/json -H "Authorization: Bearer USER_TOKEN" -v 2 http://<server_ip>:3000/api/v1/users
```

## Support

Nest is an MIT-licensed open source project. It can grow thanks to the sponsors and support by the amazing backers. If you'd like to join them, please [read more here](https://docs.nestjs.com/support).

## Stay in touch

- Author - [Kamil Myśliwiec](https://kamilmysliwiec.com)
- Website - [https://nestjs.com](https://nestjs.com/)
- Twitter - [@nestframework](https://twitter.com/nestframework)

## License

Nest is [MIT licensed](LICENSE).
