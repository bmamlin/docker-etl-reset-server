ETL Rest Server
===============

A docker container for an instance of the [ETL Rest Server](https://github.com/ampath/etl-rest-server) used by the good people at [AMPATH](https://github.com/ampath/).

Using Docker Compose 1.6+
-------------------------

### Step 1. Start containers

    docker-compose up -d

### Step 2. Profit

    curl -k https://docker:8002

Without Docker Compose
----------------------

## Building

    docker build -t etl .

## Running

### Step 1. Start a MySQL container

    docker run -d --name mysql4etl -e MYSQL_ROOT_PASSWORD=supersecret \
      -e MYSQL_USER=etl_user -e MYSQL_PASSWORD=etl_password mysql

### Step 2. Run ETL server

    docker run -d --name etl --link mysql4etl:db -p 8002:8002 etl

### Step 3. Profit

    curl -k https://docker:8002
