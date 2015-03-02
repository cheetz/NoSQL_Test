This is a test for using NoSQLMap.  The file userdata.php was a sample included in NoSQLMAP, but I had to modify it to get it to work properly.  https://github.com/tcstool/NoSQLMap

Before you can do any testing:

apt-get install php_mongo php5-dev php-pear
pear install -f pecl/mongo
pecl install mongo
pecl install apc
vi /etc/php5/apache2/php.ini
	add the following:
	extension=mongo.so
service apache2 start



vi /etc/mongodb.conf
	Edit bind port to listen on any interface
	bind_ip = 0.0.0.0

mkdir /var/www/vuln_apps
Move userdata.php to /var/www/vuln_apps

Populate the mongodb database

root@kali:~# mongo
MongoDB shell version: 2.0.6
connecting to: test
> use appUserData
switched to db appUserData
> db.createCollection("users")
{ "ok" : 1 }
> show collections
system.indexes
users
> db.users.insert({"name":"james","username":"james","email":"james@suck.testlab"})
> db.users.insert({"name":"frank","username":"frank","email":"frank@suck.testlab"})
> db.users.insert({"name":"paul","username":"paul","email":"paul@suck.testlab"})

