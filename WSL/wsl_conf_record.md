



### 使用记录：

**windows终端的一些资料：**

1. 终端文档：https://docs.microsoft.com/zh-cn/windows/terminal/

2. WSL文档：https://docs.microsoft.com/zh-cn/windows/wsl/

**WSL的一些快捷键和相关技巧：**

1. 5 tips for an awesome Windows Terminal experience：https://endjin.com/blog/2020/05/5-tips-for-an-awesome-windows-terminal-experience

2. 官方blog: https://devblogs.microsoft.com/commandline/

**2021-08-25:**






### 终端信息

Terminal: ubuntu1804
用户：johnny/空格
Root: sudo su 


### 阿里云镜像
参考文档：修改ubuntu18.04 apt源为阿里云(aliyun)镜像: https://www.cnblogs.com/Eric-Shenblog/p/10862027.html

```shell
$ mv /etc/apt/sources.list /etc/apt/sources.list.bak
$cd /etc/apt/sources.list.d/
$ sudo vim aliyun.list
# 将以下内容复制到aliyun.list中
deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse

$ apt-get update
```

### 设置 Windows 终端
教程：在 Windows 终端中设置 Powerline： https://docs.microsoft.com/zh-cn/windows/terminal/tutorials/powerline-setup

1. 安装字体
解压相应字体(.tff文件)，选中-->右键-->Install for all users
Once unzipped, right-click the font file and click "Install for all users". This will install the font onto your machine.

2. 安装Go package报错问题：

  ```shell
  root@DESKTOP-3526GM2:~# go get -u github.com/justjanne/powerline-go
  package golang.org/x/crypto/ssh/terminal: unrecognized import path "golang.org/x/crypto/ssh/terminal" (https fetch: Get https://golang.org/x/crypto/ssh/terminal?go-get=1: dial tcp 216.239.37.1:443: connect: connection refused)
  package golang.org/x/sys/unix: unrecognized import path "golang.org/x/sys/unix" (https fetch: Get https://golang.org/x/sys/unix?go-get=1: dial tcp 216.239.37.1:443: connect: connection refused)
  package golang.org/x/text/width: unrecognized import path "golang.org/x/text/width" (https fetch: Get https://golang.org/x/text/width?go-get=1: dial tcp 216.239.37.1:443: connect: connection refused)
  ```

  

3. 解决版本：
    使用GOPROXY 环境变量：

  ```shell
  export GOPROXY=https://goproxy.io
  export GO111MODULE=on
  ```

  

参考资料：https://www.cnblogs.com/shockerli/p/go-get-golang-org-x-solution.html


4. settings.json在win10中的路径：

  ```
  C:\Users\win10\AppData\Local\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState
  ```

  


5. 在T440s上出现的一个问题：

  ```shell
  johnny@T440s:~$ go get -u github.com/justjanne/powerline-go
  $ cd .; git clone -- https://github.com/justjanne/powerline-go /home/johnny/go/src/github.com/justjanne/powerline-go
  Cloning into '/home/johnny/go/src/github.com/justjanne/powerline-go'...
  fatal: unable to access 'https://github.com/justjanne/powerline-go/': Failed to connect to github.com port 443: Connection refused
  package github.com/justjanne/powerline-go: exit status 128
  ```

  解决方式:
  参考：https://blog.csdn.net/lyc_stronger/article/details/51954852
  我这里原因是：因为wsl自动在/etc/hosts中加入了github.com的地址映射，屏蔽掉就可以了。



### 命令使用go env查看go的一些全局设置
```shell
# !$:表示上一次使用的路径。
# cd !$:就是进入上一次使用的路径如：

git clone https://github.com/golang/net.git
git clone https://github.com/golang/sys.git
git clone https://github.com/golang/tools.git
git clone https://github.com/golang/crypto.git
git clone https://github.com/golang/text.git
```



