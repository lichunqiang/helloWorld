####1.在目录中查找包含文字的文件
```sh
$ grep -l -r findstring /dir
```
####2.查找文件 
```sh
$ find -type d -name .svn
```
####3.批量删除文件 
```sh
$ find -type d -name .svn | xargs rm -rf
```
####4.scp命令

