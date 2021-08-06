github在windows 10中配置ssh密钥：
参数文章： [生成新 SSH 密钥并添加到 ssh-agent](https://docs.github.com/cn/github/authenticating-to-github/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
操作步骤记录：
安装上述参考文章，操作步骤如下：
（1）生成新的ssh[生成新 SSH 密钥](https://docs.github.com/cn/github/authenticating-to-github/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key)
![image-20210806100049966](C:\Users\win10\AppData\Roaming\Typora\typora-user-images\image-20210806100049966.png)

生成如下两个文件夹：
![image-20210806100126584](C:\Users\win10\AppData\Roaming\Typora\typora-user-images\image-20210806100126584.png)

（2）将 SSH 密钥添加到 ssh-agent
![image-20210806100534813](C:\Users\win10\AppData\Roaming\Typora\typora-user-images\image-20210806100534813.png)

（3）将ssh密钥添加到github账户
<img src="C:\Users\win10\AppData\Roaming\Typora\typora-user-images\image-20210806101052809.png" alt="image-20210806101052809" style="zoom:67%;" />

测试报如下错误：
![image-20210806102003422](C:\Users\win10\AppData\Roaming\Typora\typora-user-images\image-20210806102003422.png)
![image-20210806103304727](C:\Users\win10\AppData\Roaming\Typora\typora-user-images\image-20210806103304727.png)

错误解决办法：
参考资料： [在HTTPS端口使用SSH：](https://docs.github.com/cn/github/authenticating-to-github/troubleshooting-ssh/using-ssh-over-the-https-port)
![image-20210806112244712](C:\Users\win10\AppData\Roaming\Typora\typora-user-images\image-20210806112244712.png)

这样配置之后，可以使用https的方式提交项目