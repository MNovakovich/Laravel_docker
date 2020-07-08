
## Docker running Laravel app

**Initial docker setup is with Apache server!**

- Step 1: clone project
- Step 2: cd into project root
- Step 3 : Into the root of project clone laravel app from official github repo : https://github.com/laravel/laravel 
  
  ``` git  clone https://github.com/laravel/laravel.git```
   Rename folder ***laravel***  to ***src***

  ### Notice ###
    * If you using alredy existed laravel project, just create ***src*** folder and put it into.

- Step 4: Into src folder create .env file in project  and copy structure from .env.example, 
  
     ### Notice ###
   Into the ```/src/.env``` file next constants must be same as constants into the ```env ``` from root of project:
   ```
    DB_CONNECTION=mysql
    DB_HOST=db
    DB_PORT=3306
    DB_DATABASE=homestead
    DB_USERNAME=homestead
    DB_PASSWORD=secret

   ```
- Step 5: Build project, run ```docker-compose build```
  ***Notice*** If you change a service’s Dockerfile or the contents of its build directory, you should run the same command again to rebuild it.
- Step 6: ```docker-compose up -d``` (for detached mode)

  Install composer, run ```docker-compose run 'service_name' composer install```
- Step 7: The next thing you should do after installing Laravel is set your application key. 
  
    Generate app key, run ```docker-compose run 'service_name' php artisan key:generate```



Containers created and their ports are as follows:

- **php** - `http://localhost:8001`
- **phpmyadmin** - `http://localhost:8005`
  
## How To! ##

### Use ***nginx*** server: ###
If you want to use Nginx server -> copy and replace files from ./docker-files-nginx into project root. \
In that case, link for browser is: http://localhost:8001  

***Notice!***
 - If you want to use Apache server again -> copy and replace files from ./docker-files-apache into project root.

-  Before changing server environment, you must run following command: docker-compose down

### get your containers Ip addresses. From your docker host ###
  ```docker inspect -f '{{.Name}} - {{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' $(docker ps -aq)```