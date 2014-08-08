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

## 介绍下如何让你的一个项目在多个git平台共同存在

我们知道在git初始化的时候会执行下面的语句：
```sh
$ git remote add origin git@github.com:xx/xx.git
```
在当我们进行提交的时候会执行：
```sh
$ git push origin master
```

以前不知道这个用意，但是当我们需要将这个项目推送到多个git平台时，其中奥妙则显现出来了。

比如先有有个第三方git平台，如`git@git.oschina.net`,我们同时也希望把此项目推送到这里。那么我们可以采用以下方法：
```sh
$ git remote add new_origin git@git.oschina.net
```
接下来我们就可以将项目推送到此平台（前提是已经在该平台建好项目）
```sh
$ git push new_origin master
```
__Done__

同样当进行其他操作的时候，我们需要推送到`git@git.oschina.net`的时候就需要使用新的了，如新建`tag`

```sh
$ git tag 1.0.0
$ git push new_origin 1.0.0
```
写在最后：同样我们可以利用`rename`来转换项目的平台,即将`new_origin` 重命名为 `origin`, 操作就和以前一样啦！
