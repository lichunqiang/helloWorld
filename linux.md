###1.在目录中查找包含文字的文件
```
$ grep -l -l findstring /dir
```
###2.查找文件 
```
$ find -type d -name .svn
```
###3.批量删除文件 
```
$ find -type d -name .svn | xargs rm -rf
```