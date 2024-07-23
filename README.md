# Services for locale Development

* MariaDB 10.9.3
* MariaDB 10.6.16
* Redis 7.2.4
* MongoDB 7.0.12
* PHP-FPM 8.2.21 for CodeSniffer
* S3Mock 3.5.2
* S3Mock 3.6.0
* min.io RELEASE.2024-06-29T01-20-47Z

## Installation

### Clone project

```bash
git clone git@github.com:alaugks/docker-local.git
```

### Run docker compose

```bash
docker compose up -d
```

## Example of usage (MariaDB 10.9.3)

### Example Symfony

**.env.local**

```dotenv
DB_DRIVER=mysql
DB_USER=dev-user
DB_PASSWORD=dev-password
DB_HOST=mariadb-10-9-3
DB_PORT=3306
DB_NAME=your_database
DB_SERVER_VERSION=10.9.3-MariaDB
```

**services.yaml**

```yaml
parameters:
  database_url: '%env(DB_DRIVER)%://%env(DB_USER)%:%env(DB_PASSWORD)%@%env(DB_HOST)%:%env(DB_PORT)%/%env(DB_NAME)%?serverVersion=%env(DB_SERVER_VERSION)%'
```

### Example Spring Boot

**application.properties**

```dotenv
spring.datasource.url=jdbc:mariadb://mariadb-10-9-3:3306/your_database
spring.datasource.username=dev-user
spring.datasource.password=dev-password
spring.datasource.driver-class-name=org.mariadb.jdbc.Driver
```

## Use CodeSniffer in PHPStorm

**Settings CLI Interpreters**

![CLI_Interpreters.png](docs/CLI_Interpreters.png)


**Settings PHP CodeSniffer**

![PHP_CodeSniffer.png](docs/PHP_CodeSniffer.png)


**Path Code Sniffer**

```
/var/www/html/vendor/squizlabs/php_codesniffer/bin/phpcs
```


**Path Code Beautifier**

```
/var/www/html/vendor/squizlabs/php_codesniffer/bin/phpcbf
```
