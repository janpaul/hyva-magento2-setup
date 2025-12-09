# Magento2 + Hyvä Clean Install

## Pre-setup

### Install docker

Do it here at [docker](https://docs.docker.com/get-docker/).

### Create the 'src' directory
Make sure you have a `src` directory in the current directory. This can (and should) be empty.

```shell
mkdir src
```

## Get Magento2 authentication keys

### Create an Adobe Commerce account

Create an Adobe Commerce account [here](https://account.magento.com/register).

### Get your authentication keys

- Go to [Magento Marketplace](https://marketplace.magento.com/customer/accessKeys/).
- Log in with your Adobe Commerce account
- Navigate to "My Profile"
- Go to the "Access Keys" tab
- Create a new set of keys for Magento Open Source
- Copy the Public Key and Private Key, you will need them later!

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

### Get Magento2

Run the following command:

```shell
composer create-project \
  --repository-url=https://repo.magento.com/ \
  magento/project-community-edition .
```

You will be prompted to enter your username and password. Use the Public Key as username and the Private Key as 
password.

Sadly, you may need to run the command multiple times until all packages are downloaded.

### Install Magento2

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

## Access Magento2

You can now access your Magento2 installation at [http://localhost:8080](http://localhost:8080).
