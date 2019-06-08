# Original readme info
Visit project web site [http://connfa.com/](http://connfa.com/)

Documentation is available on [http://connfa.com/documentation](http://connfa.com/documentation)

API documentation is available on [http://connfa.com/api](http://connfa.com/api)

Project is supported by [Lemberg Solutions](http://lemberg.co.uk)

# Getting started
To start using the connfa-server you first need to copy the `.env.example` file into `.env`.
The environment variables in this file hold the settings of your site.

### Mandatory parameters
The database parameters (self explanatory):
* DB_HOST
* DB_PORT
* DB_DATABASE
* DB_USERNAME
* DB_PASSWORD

### Cache driver
The cache driver `CACHE_DRIVER`. There are many possible values including `redis`, `memcache`
`file`, `array` etc. You will probably need a cache driver for production. For testing
purposes, `array` will suffice.

### Other parameters
The rest of the parameters work almost out of the box for testing. However, they need to be set at
some point too.

# Installation
### Setting the key
In the `.env` file there is a variable called `APP_KEY`. This value is also mandatory.
To generate a key, run the following command:
```bash
php artisan key:generate
```
It will generate a key and set it in the `.env` file.

### Installation of the database
The database structure is stored in the `./databse/migrations` folder. To install (migrate) this list of tables
structure to your database run:
```bash
php artisan migrate:install
```
An empty database will be installed.

### Resetting/refreshing the database
To clean the database from all tabels run:
```bash
php artisan migrate:reset
```
This will rollback the database to a state without the tables.
If instead you want to reinstall the database, run:
```bash
php artisan migrate:refresh
```
This is merely a shortcut for the `migrate:reset` and the `migrate:install`

### Seeds
Seeds are predefined data that can populate the database. Some data are needed, for example
routes and roles, and some are test data available to be imported. The list of currently available
seets are in the `./database/seeds` directory.

#### Test database
To install a complete database with data of all types, you need to populate the database
with all available seeds. To do so, run:
```bash
php artisan db:seed
```

#### Basic structure
To install without the test data, just roles, an admin user account, the event levels etc, run:
```bash
php artisan db:seed --class=CleanDatabaseSeeder
```