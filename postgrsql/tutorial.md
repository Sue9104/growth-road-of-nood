# 数据库搭建教程
## 单个数据库

## 多个端口数据库

- .env文件
```sh
# Docker specific configs
# use only letters and numbers for the project name
COMPOSE_PROJECT_NAME=genecard
# Global configs
DEVELOPMENT=1
JWT_SECRET=secret
TZ=Asia/Shanghai
# DB connection details (used by all containers)
DB_EXPOSE_PORT=5437
DB_NAME=pharmgkb
DB_SCHEMA=public
DB_USER=postgres
DB_PASS=123456
POSTGREST_PORT=32581
# PostgREST
DB_ANON_ROLE=postgres
DB_POOL=10
#MAX_ROWS=
#PRE_REQUEST=
```

- docker-compose.yaml
```sh
version:         '2'
services:
  # PostgREST instance, is responsible for communicating with the database
  # and providing a REST api, (almost) every request that is sent to the database goes through it
  api:
    image:       subzerocloud/postgrest
    ports:
      - ${POSTGREST_PORT}:3000
    links:
      - db:db
    environment:
      - PGTZ=${TZ}
      - DB_URI=postgres://${DB_USER}:${DB_PASS}@db:5432/${DB_NAME}
      - DB_SCHEMA=${DB_SCHEMA}
      - DB_ANON_ROLE=${DB_ANON_ROLE}
      - DB_POOL=${DB_POOL}
      - JWT_SECRET=${JWT_SECRET}
      - MAX_ROWS=${MAX_ROWS}
      - PRE_REQUEST=${PRE_REQUEST}
  sqitch:
    image: jmabey/sqitch:postgres-sh
    entrypoint:
      - ./init.sh
    volumes:
      - ./sqitch:/src:Z
      - ./data:/data:ro
    environment:
      - PGTZ=${TZ}
      - PROJECT=${COMPOSE_PROJECT_NAME}
      - DB_URI=postgres://${DB_USER}:${DB_PASS}@db:5432/${DB_NAME}
    command:
      - deploy
  db:
    image: postgres
    restart: always
    ports:
      - ${DB_EXPOSE_PORT}:5432
    volumes:
      - ./db:/var/lib/postgresql/data
    environment:
      # env vars specific to postgres image used on first boot
      - POSTGRES_USER=${DB_USER}
      - POSTGRES_PASSWORD=${DB_PASS}
      - POSTGRES_DB=${DB_NAME}
```


