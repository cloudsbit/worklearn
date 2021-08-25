值得仔细连接的github入门指南：https://docs.github.com/cn/github/getting-started-with-github/quickstart/set-up-git



### github在md文档中插入图片

使用相对地址，而非绝对地址，这样本地和github上显示都可以， 如：![image-20210825101954326](images\image-20210825101954326.png)



### github在windows 10中配置ssh密钥

参数文章： [生成新 SSH 密钥并添加到 ssh-agent](https://docs.github.com/cn/github/authenticating-to-github/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
操作步骤记录：
安装上述参考文章，操作步骤如下：
（1）生成新的ssh[生成新 SSH 密钥](https://docs.github.com/cn/github/authenticating-to-github/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key)
![image-20210806100049966](images\image-20210806100049966.png)

生成如下两个文件夹：
![image-20210806100126584](images\image-20210806100126584.png)

（2）将 SSH 密钥添加到 ssh-agent
![image-20210806100534813](images\image-20210806100534813.png)

（3）将ssh密钥添加到github账户
<img src="images\image-20210806101052809.png" alt="image-20210806101052809" style="zoom:67%;" />

测试报如下错误：
![image-20210806102003422](images\image-20210806102003422.png)
![image-20210806103304727](images\image-20210806103304727.png)

错误解决办法：
参考资料： [在HTTPS端口使用SSH：](https://docs.github.com/cn/github/authenticating-to-github/troubleshooting-ssh/using-ssh-over-the-https-port)
![image-20210806112244712](images\image-20210806112244712.png)

windows的配置(~/.ssh/config or C:\Users\win10\.ssh\config)如下：
![image-20210806113137876](images\image-20210806113137876.png)

这样配置之后，可以使用https的方式提交项目，使用密钥的方式：
参考资料：[管理远程仓库](https://docs.github.com/cn/github/getting-started-with-github/getting-started-with-git/managing-remote-repositories)
![image-20210806113029700](images\image-20210806113029700.png)

