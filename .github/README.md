<p align="center">A Docker PHP development environment that facilitates running PHP Apps on Docker</p>


<h4 align="center" style="color:#7d58c2">Use Docker First And Learn About It Later</h4>

<p align="center">
    <a href="https://zalt.me"><img src="http://forthebadge.com/images/badges/built-by-developers.svg" alt="forthebadge" width="240" ></a>
</p>


##Custom setup for memcache
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
