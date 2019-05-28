---
title: git clone时报错Permission denied (publickey,password)
---

> 在使用`git clone xxxx`时，报错，如图

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190528213122663.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZhbnRhc2ljX3Zhbg==,size_16,color_FFFFFF,t_70)


###  1、上网查资料，说可能是SSH Key不存在

使用命令`ls ~/.ssh/`，可以看到，SSH key是存在的，所以这种情况排除

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190528213146927.png)

### 2、按github官网：

#### 1）、Ensure the ssh-agent is running:

```shell
#start the ssh-agent in the background
$ eval $(ssh-agent -s)
> Agent pid 59566
```



####  2）、Add your SSH private key to the ssh-agent

```shell
$ ssh-add ~/.ssh/id_rsa
```

#### 3）、添加ssh key到github
![在这里插入图片描述](https://img-blog.csdnimg.cn/201905282132333.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZhbnRhc2ljX3Zhbg==,size_16,color_FFFFFF,t_70)
  
复制
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190528213244818.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZhbnRhc2ljX3Zhbg==,size_16,color_FFFFFF,t_70)

文件中的内容，粘贴保存。

####  4）、测试连接

  `ssh -vT git@github.com` ,显示成功。

### 3、重新`git clone xxx`，成功执行



### 总结： 重新添加了ssh key就成功了。


