# Docker-demo-app

Just test for myself

# Config

react-ts-app フォルダと同じ階層に下記のファイルを作成。

## docker-compose.yml

```yml: docker-compose.yml
version: "3"
services:
  node:
    build:
      context: .
    volumes:
      - ./:/react-ts-app
    command: sh -c "cd react-ts-app && npm start"
    ports:
      - "3000:3000"
```

## Dockerfile

```Dockerfile
FROM node:18-alpine3.14
ENV NODE_VERSION 14.18.1
WORKDIR /react-ts-app
COPY ./react-ts-app /react-ts-app
EXPOSE 3000
ENV CI=true
```
