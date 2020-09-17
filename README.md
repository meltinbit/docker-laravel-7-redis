## MAIN INSTALLATION

### For an Existing or New Laravel 7 project

```bash
git clone repo_projectname or laravel new projectname or composer create-progect laravel/laravel projectname
cd repo_projectname
composer install
php artisan key:generate
cp .env.example .env #set the DB credentials

git clone https://github.com/meltinbit/docker-laravel-7-redis.git docker-compose
cd docker-compose/scripts
./dcup.sh #to start containers
./dcdown.sh #to stop containers
#modifify services names and ports if necessary
```

## DOCKER

### DOCKER USEFUL COMMAND
```bash
docker-compose ps #list active containers in this folder
docker-compose restart 
docker exec -it dbcontainername mysql -u root -p //enters the mysql client
docker exec -i dbcontainername mysql -u root -p123456 dbnameinenv < database.sql
```

## COMPOSER INSTALL
To run `composer install` for a existing project enter the project folder and run:
```bash
docker run --rm -v $(pwd):/app composer install
```

### MEMORY PROBLEMS ON LINUX WITH COMPOSER INSTALL
A swap file is needed. Run the following commands:

```bash
swapon --show
fallocate -l 1G /swapfile
dd if=/dev/zero of=/swapfile bs=1024 count=1048576
chmod 600 /swapfile
mkswap /swapfile
swapon /swapfile
nano /etc/fstab and add the line: /swapfile swap swap defaults 0 0
swapon --show
```
