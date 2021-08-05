# db-api

* 使用docker搭建pg数据库
* sqitch进行数据库管理

## 单个数据库

## 多个数据库

> 使用docker-compose进行数据库搭建、sqitch管理、提供API端口，形成一个完成的流程

### 准备配置文件

* .env文件

  ```bash
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

* docker-compose.yaml

  ```bash
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

* sqitch/init.sh

  ```bash
  #!/usr/bin/env sh
  test_uri() {
  echo select 1 | psql $DB_URI > /dev/null
  }
  while ! test_uri;
  do
  sleep 2
  done
  export ANSI_COLORS_DISABLED=1
  # init or not
  if [ ! -f sqitch.plan ]; then
  echo %project=$PROJECT > sqitch.plan
  chmod 766 sqitch.plan
  fi
  # config
  cat > sqitch.conf << EOL 
  [target "production"]
  uri = $DB_URI
  [core]
  engine = pg
  [rebase]
  verify = true
  [deploy]
  verify = true
  [engine "pg"]
  target = production
  [user]
  name = Su Min
  email = sumin@cheerlandgroup.com
  EOL
  if [ "$1" = 'sh' ]; then
  echo "Run bash command"
  $@  
  elif [ "$1" = "load" ]; then
  echo "Load data from /data"
  ls -al /data
  if [ "$2" = "" ]; then
    echo "You must select which data to load!"
    echo ""
    echo "Here's the support data list:"
    ls load | grep '.sql' | sed 's/.sql//' | xargs -i echo {}
    echo ""
  else
    cat load/${2}.sql | psql $DB_URI
  fi  
  else
  sqitch $@
  fi
  ```

  **运行命令**

  ```text
  docker-compose up -d
  ```

  **用sqitch添加schema、table**

  ```text
  sqitch add schema -n 'add schema'
  sqitch verify
  sqitch deploy
  sqitch revert
  ```

