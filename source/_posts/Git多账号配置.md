---
title: 如何在一台电脑配置多个Git账户
date:  2017-04-28 11:30:19
tags:
---

[Git](https://git-scm.com/)相比大家已经不陌生了，也许是现在用的最多的版本控制工具了。

这里我不对Git的使用做过多的说明，如果你还没用过Git的话，我建议你先去学习下吧，对你会有很大的帮助，这里我奉上 [廖雪峰的Git教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)。

同时我这里操作的平台是MacOS，当然不同的平台会有稍微的不同，不过我相信通过度娘，你都可以得到解决。

今天我主要来说一下，在一台电脑上设置多个Git账号。


<!--more-->

在`~/.ssh`目录下保存所有生成的密钥，建立`config`文件。

```bash
$ vim ~/.ssh/config
```

config文件内容如下：

```
Host github.com
HostName github.com
User xiaoming
IdentityFile ~/.ssh/id_rsa

Host iuunhao
HostName github.com
User iuunhao
IdentityFile ~/.ssh/id_rsa_iuunhao
```

```bash
　$ ssh-keygen -t rsa -C "email"
 ```
  我们在生成ssh的时候在第一项填写一个名字`id_rsa_iuunhao`
  
  在`config`文件里的`IdentityFile`面需要对调用对应的文件。
  
  而`HostName`这里需要修改对应的`id_rsa_iuunhao`
  
  这个时候我们在clone项目的时候，`github.com`代表默认的`ssh key`就是在生成`ssh key`的时候没有填写任何内容那个用户
  
  如果是`iuunhao`用户，那在clone的时候需要修改一下地址
  
 原的地址：
 ```bash
 git@github.com:iuunhao/demos.git
```

修改为
```bash
git@iuunhao:iuunhao/demos.git
```

这里的`xiaoming`是默认用户，正常clone项目就可以使用。

全局的git `user.name`及`user.email`都配置的是`xiaoming`的信息

但是需要用`iuunhao` 提交代码的时候需要注意，我们需要手动设置该项目的

需要注意的是`User`这个内容要填写你的github用户名，其实就是git的`user.name`及`user.email`

```bash
git config user.name "username"
git config user.email "email"
```
需要注意的这里取消` --global`参数。

如果不注意这点的话，提交代码没问题，但是显示的信息，就不对了。

会出现这样的情景。
![](http://ww3.sinaimg.cn/large/006tNbRwly1ff2bd6m6paj30ql05ejrz.jpg)

