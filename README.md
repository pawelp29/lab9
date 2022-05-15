# lab9
Simple LEMP stack constructed with 4 Docker containers.

## *php-fpm* container configuration
- `DocumentRoot` directory mounted with *bind mount* in `/var/www/html` - it contains a simple PHP script shwing `phpinfo()`
- Statically assigned IP 172.20.0.10 in `backend` network
- Port forwarding from 9000 to 9000

## *nginx* container configuration
- `nginx` directory mounted with *bind mount* in `/etc/nginx/conf.d` - it contains a config file responsible for connection with *php-fpm*
- Connected to `backend` and `frontend` networks
- Port forwarding from 8000 to 80

## *mariadb* container configuration
- *mariadb-volume* mounted at `/var/lib/mysql` - this volume will contain the database contents
- Connected to `backend` network
- Environment variables responsible for example database user login credentials

## *phpmyadmin* container configuration
- Connected to `backend` network
- Port forwarding from 6001 to 80
- Link to *mariadb* container

## *backend* network configuration
- Subnet 172.20.0.0/16
