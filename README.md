# mysql-build-env

Building environment of mysql-server.

## Example

### Docker

```
$ git clone git@github.com:mysql/mysql-server.git
$ (cd mysql-server; git checkout 8.0)
$ docker run --rm -it --user $(id -u):$(id -g) -v $(pwd)/mysql-server:/mysql-server usualoma/mysql-build-env:8.0-ubuntu cmake .
$ docker run --rm -it --user $(id -u):$(id -g) -v $(pwd)/mysql-server:/mysql-server usualoma/mysql-build-env:8.0-ubuntu make
$ mkdir data
$ docker run --rm -it --user $(id -u):$(id -g) -v $(pwd)/mysql-server:/mysql-server -v $(pwd)/data:/data usualoma/mysql-build-env:8.0-ubuntu sql/mysqld --basedir /mysql-server/sql --datadir /data --initialize-insecure
$ docker run --rm -it --user $(id -u):$(id -g) -v $(pwd)/mysql-server:/mysql-server -v $(pwd)/data:/data usualoma/mysql-build-env:8.0-ubuntu sql/mysqld --basedir /mysql-server/sql --datadir /data
```

### Vagrant

```
$ git clone git@github.com:mysql/mysql-server.git
$ (cd mysql-server; git checkout 8.0)
$ curl https://raw.githubusercontent.com/usualoma/mysql-build-env/master/8.0/ubuntu/Vagrantfile > Vagrantfile
$ vagrant up
$ vagrant ssh
$ cd /mysql-server
$ cmake .
$ make
$ mkdir ~/data
$ ./sql/mysqld --basedir /mysql-server/sql --datadir ~/data --initialize-insecure
$ ./sql/mysqld --basedir /mysql-server/sql --datadir ~/data
```
