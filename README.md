# Magento2 + Hyvǎ Clean Install

## Pre-setup

Make sure you have a `src` directory in the current directory. This can (and should) be empty.

```shell
mkdir src
```

## Install docker

Do it here at [docker](https://docs.docker.com/get-docker/).

## Start the containers

Start the containers with the following command:

```shell
docker-compose up -d
```

## Install Magento2

Access the container with the following command:

```shell
docker exec -it magento-php bash
```

Install Magento2 with the following command:

```shell
bin/magento setup:install \
  --base-url=http://localhost:8080 \
  --db-host=db \
  --db-name=magento \
  --db-user=magento \
  --db-password=magento \
  --backend-frontname=admin \
  --admin-firstname=Admin \
  --admin-lastname=User \
  --admin-email=admin@example.com \
  --admin-user=admin \
  --admin-password=Admin123! \
  --search-engine=opensearch \
  --opensearch-host=opensearch \
  --opensearch-port=9200
```
