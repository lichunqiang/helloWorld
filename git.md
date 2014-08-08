[同步fork的代码](https://help.github.com/articles/syncing-a-fork)


## 多个平台git共存

1.设置用户名和邮件地址

```sh
$ git config --global user.name "xx"

$ git config --global user.email "test@gmail.com"
```

2. 生成ssh-key

> ssh-key保存在`~/.ssh文件中

```sh
ssh-keygen -t rsa -C "test@gmail.com"
```
在选择保存key文件的时候，可以重名，当多个git平台的时候非常重要。

3. 将生成的ssh-key即xxx.pub文件内容保存到git平台的`ssh`公钥中。

4. 配置config.
 
打开`~/.ssh`文件中的`config`文件，添加多个平台信息和对应key，如下

```
Host github.com-lichunqiang
    Hostname github.com
    User git
    IdentityFile ~/.ssh/id_rsa
Host git.oschina.net-light-li
    Host git.oschina.net
    User git
    IdentityFile ~/.ssh/id_o_oschina
Host coding.net-light
    Host coding.net
    User git
    IdentityFile ~/.ssh/id_coding
```

最后就是按照在git平台的初始化项目进行使用了。
