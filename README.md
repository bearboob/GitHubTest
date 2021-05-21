# 如何用Git将代码上传到Github

## 前言

本文以windows为例教大家如何使用Git把代码上传到Github。



## 下载工具

前往官网（https://gitforwindows.org/ ）下载Git安装包。下载完成之后，一路点击“Next”就完成安装了。



## 配置身份

在桌面或者“开始”找到GitBash并打开，配置一下身份，这样提交代码的时候，Git就知道是谁提交的了。配置命令如下

```
git config --global user.name "bearboob"

git config --global user.email "316510202@qq.com"
```

把里面的"bearboob"与"316510202@qq.com"替换成你自己的用户名以及邮件就可。这样就配置好了。

再来检查一下是否配置成功，命令如下

```
git config --global user.name

git config --global user.email
```

运行结果如下

<img src="https://github.com/bearboob/GitHubTest/blob/main/pic/001.png">

这样就是配置成功了。

## 在Android Studio创建项目

这部分就直接上图了。

<img src="https://github.com/bearboob/GitHubTest/blob/main/pic/010.png">

## 在GitHub上创建仓库

首先你得注册一个GitHub账号。（注：现在可能需要科学上网，才能流畅访问GitHub。）

进入GitHub官网（https://github.com/ ）， 点击右上角的Sign up注册一个账号。然后登陆刚刚注册的账号，就能看到下面这个页面

<img src="https://github.com/bearboob/GitHubTest/blob/main/pic/002.png">

点击"Start a project"，进入创建项目的界面

<img src="https://github.com/bearboob/GitHubTest/blob/main/pic/003.png">

依次填入仓库名称（Repository name)。可以加一下仓库描述，如果你要公开就选择Public，如果不想给别人看到就选Private。下面三个可以都勾选上。

我做Android，就都勾选上，选择相应的内容就行。

其中.gitignore这个文件里写的内容，是不加入版本控制的。填入相应内容，我们选择"Create repository"就可。

<img src="https://github.com/bearboob/GitHubTest/blob/main/pic/004.png">

创建好之后，点击"Code"可以看到一个网址。复制这个网址（https://github.com/bearboob/GitHubTest.git） （你替换成你的就行。）

<img src="https://github.com/bearboob/GitHubTest/blob/main/pic/005.png">

## 代码上传

在GitBash中进入我们刚刚创建的Android 项目（E:\AndroidStudioProjects\GitHubTest），输入命令

```
git clone https://github.com/bearboob/GitHubTest.git
```

这个网址就是我们上面复制的那个。

<img src="https://github.com/bearboob/GitHubTest/blob/main/pic/006.png">

这样就把GitHub上的代码克隆到本地了。进入E:\AndroidStudioProjects\GitHubTest\GitHubTest 输入

```
ls -al
```

 可以看到目录下有这些内容

<img src="https://github.com/bearboob/GitHubTest/blob/main/pic/007.png">

我们进入E:\AndroidStudioProjects\GitHubTest\GitHubTest,把这里的内容全部拷贝到外面这一层目录（E:\AndroidStudioProjects\GitHubTest），**.git文件夹不能漏掉了**。

然后把E:\AndroidStudioProjects\GitHubTest\GitHubTest 删掉就行了。

进入 E:\AndroidStudioProjects\GitHubTest，输入命令

```
git add .
```

这样把当前文件夹下的所有文件，加入版本控制。

```
git commit -m "commit initial code"
```

执行提交操作。其中“ ”中的内容，由你自定义，这个是我们每次提交代码时的日志。最后

```
git push origin main
```

就可以把提交的内容同步到GitHub上了。在这一步，会要求填GitHub的用户名和密码来进行校验。

<img src="https://github.com/bearboob/GitHubTest/blob/main/pic/008.png">

我们再去GitHub上刷新一下

<img src="https://github.com/bearboob/GitHubTest/blob/main/pic/009.png">

成功啦。



## 可能出现的错误

在最后一步，可能出现的错误有

```
 error: RPC failed; curl 92 HTTP/2 stream 0 was not closed cleanly: PROTOCOL_ERROR (err 1)
```

这个这样解决

```
git config --global http.version HTTP/1.1  
```

如果还不行，再加大一下缓存

```
git config --global http.postBuffer 524288000
```

如果还不行，就很可能是科学上网的网速不行了。

因为我上午操作同样的内容，传不上去。下午，又传上去了。


## 总结

这里要注意的就是科学上网。如果访问不流畅，可能在最后一步总是出错，导致上传不成功。



