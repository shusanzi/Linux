# windows10自带Linux

## windows设置
1、启动开发者模式（会下载大概1g的文件）

2、启动Linux组件：

系统设置 -> 应用 -> 右侧的程序和功能 -> 启动或关闭windows功能 -> 勾选适用于 Linux 的 Windows 子系统

3、重启后，商店下载Ubuntu

[参考](https://blog.csdn.net/zhouzme/article/details/78780479)

> 注意：CMD 总是会遇到不会自动刷新输出内容卡在那儿不动，一直显示安装中，实际初始化是很快的。


## Ubunto设置
1、输入用户名 密码
> 用户名不能用root（我设置的时候就不能用） 密码的话输入没有反应，其实是有的，只是不显示。

2、查看版本
```
lsb_release -a
```

## 图形界面
图形界面找了很久，有两种方法：
- 使用Windows10本机远程桌面连接
- 使用Xming及ssh连接

相同点是：两者都需要先在powershell或者cmd中先启动bash。

不同点是：远程桌面的方法启动bash后再启动远程桌面，只用配置一次，以后点击链接就可以，相当于每次启动需要鼠标点击一次powershell，输入bash，点击远程桌面，点击链接；

xming的方法需要再启动xming，然后在powershell里输入DISPLAY=:0 starxfce4，但是终端都会记录以前输入的内容，所以也不用每次都输入，其实就我个人而言，xming的方法更加方便启（zhuang）动(bi)，哪怕每次都输入DISPLAY=:0 startxfce4。

使用远程桌面的方法启动后，可以关掉powershell了，只要后台服务在运行，就不会影响体验，但是xming不行，如果刚刚那个启动xfce4的powershell关掉，所有打开的窗口都会关闭。

[参考](http://baijiahao.baidu.com/s?id=1596652006568524478&wfr=spider&for=pc)

最后使用远程链接方法，但仍然需要安装Xming等图形界面。

### Ubunto图形界面方法

1、在Ubunto中，输入：
```
更新
sudo apt-get update
安装 xorg
sudo apt-get install xorg
安装xfce4
sudo apt-get install xfce4
安装xrdp
sudo apt-get install xrdp
配置xrdp
sudo sed -i 's/port=3389/port=3390/g' /etc/xrdp/xrdp.ini

向xsession中写入xfce4-session
sudo echo xfce4-session >~/.xsession
重启xrdp服务
sudo service xrdp restart
如果有防火墙，允许就好了

```


2、在Cortana中搜索远程桌面连接，点击进入，输入本机IP：端口，以及子系统用户名（在步骤2中，终端窗口@符号之前）

[参考](https://jingyan.baidu.com/article/ed2a5d1f98577809f6be17a3.html)