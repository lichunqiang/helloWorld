Apache 
============

###查看apache读取的配置文件
```
$ ps -ef | grep apache      ---or httpd
apache   17183 17181  0 18:38 ?        00:00:00 /usr/sbin/httpd
```
```
$ /usr/sbin/httpd -V | grep SERVER_CONFIG_FILE
 -D SERVER_CONFIG_FILE="conf/httpd.conf"
```

