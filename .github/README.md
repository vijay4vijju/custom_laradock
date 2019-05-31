<p align="center">A Docker PHP development environment that facilitates running PHP Apps on Docker. Base was from laradock</p>


<h4 align="center" style="color:#7d58c2">Use Docker First And Learn About It Later</h4>

##Changes

1. Copy .env.example 
```cp .env-example .env```

2. Change `APP_CODE_PATH_HOST` key in .env file if required.

3. Configure nginx sites based on your paths same hosts name update in docker-compose.yml under nginx networks. 

4. Run docker compser up

```
docker-compose bulid -d nginx mysql phpmyadmin redis workspace memcached beanstalkd beanstalkd-console

docker-compose up -d nginx mysql phpmyadmin redis workspace memcached beanstalkd beanstalkd-console

```

##Additional .env changes required in all repositoroies

1. For mysql host use `mysql` instead `127.0.0.1`

2. For Redis host use `redis` instead `127.0.0.1`


##Stop the services
```docker-compose down # to stop the docker```

##Ssh to workspace to run composer update and migrations

```docker-compose exec workspace bash```


##Custom setup for memcache
```code
apt-get update 
apt-get install wget
wget https://github.com/websupport-sk/pecl-memcache/archive/NON_BLOCKING_IO_php7.zip

unzip NON_BLOCKING_IO_php7.zip

cd pecl-memcache-NON_BLOCKING_IO_php7

apt-get install zlib1g-dev

phpize && ./configure --enable-memcache && make

cp -r modules /usr/lib/php/modules/

vi /etc/php/7.2/cli/php.ini

#add this line at the end
extension=/usr/lib/php/modules/memcache.so

rm -rf NON_BLOCKING_IO_php7.zip pecl-memcache-NON_BLOCKING_IO_php7
```

for more documentation refer https://laradock.io/
