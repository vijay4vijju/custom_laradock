<p align="center">A Docker PHP development environment that facilitates running PHP Apps on Docker. Base was from laradock</p>


<h4 align="center" style="color:#7d58c2">Use Docker First And Learn About It Later</h4>
##Changes

1. Copy .env.example 
```cp .env.example .env```

2. Change `APP_CODE_PATH_HOST` key if required.

3. Configure nginx sites based on your paths same hosts name update in docker-compose.yml under nginx networks. 






##Custom setup for memcache
```code
apt-get install wget

wget http://pecl.php.net/get/memcache-2.2.4.tgz

tar -zxvf memcached-2.2.4.tgz

cd memcached-2.2.4

apt-get install zlib1g-dev

phpize && ./configure --enable-memcache && make

cp modules/memcache.so /usr/lib/php/modules/

Note: packaged extension modules are now loaded via the .ini files
found in the directory /etc/php.d

touch /etc/php.d/memcached.ini

echo 'extension=memcache.so' > /etc/php.d/memcached.ini
```
