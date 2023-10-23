# VPS介绍

<aside>
💡     要想进行节点的搭建，首先就需要有一台自己的VPS，需要那个国家的节点就买那个国家的VPS。VPS通俗的讲可以理解成是在地球上某一个机房里面24H不关机的一个电脑，租用后可以在家里进行远程操作，会得到一个公网IP

</aside>

# 1、系统介绍

1. **Windows系统** 可以采用远程桌面3389端口进行操作，就像一台普通的电脑一样
    1. 存在图形化操作界面，所以资源站哟高
    2. 本身是微软的闭源操作系统，要收费，价格高
2. **LInux系统** 是最常用的操作系统，使用[SSH工具](https://www.hostbuf.com/t/988.html) 的22端口进行管理
    1. 主要包括**Ubuntu、CentOS、debian、欧拉**等
    2. 软链接：bin目录下，相当于Windows下的快捷方式
    3. 常用指令
        1. restart 应用——重启某个应用
        2. status 应用——查看某个应用的状态
        3. ufw disable——关闭Ubuntu的防火墙，本机外围防火墙≠GFW
    
    ![](https://pomf2.lain.la/f/hb4lfl27.jpg)
    
    ![](https://pomf2.lain.la/f/idecmr1.png)
    
    > 本文的介绍基于**Ubuntu**操作系统，后期会加上**X-UI**

# 2、配置

![](https://pomf2.lain.la/f/hb4lfl27.jpg)

> 在SSH工具上配置好购买的VPS的IP和用户名（通常为root）、密码

![](https://pomf2.lain.la/f/idecmr1.png)

![](https://pomf2.lain.la/f/ss46dioh.png)

# 3、加密方法

> 密码和加密方式也可以不改，配置客户端时要保持一致
> 
- **对称加密算法**：加密密钥和解密密钥相同
- **加密方式**：GCM——身份验证（**AEAD**）
- **对称加密算法**：私钥加密，公钥解密

> **server**需要更改成在ss模式下使用的**0.0.0.0** 意为接收所有IP的请求，默认只接受本机的IP请求
> 

> 在v2ray中Tcping测速——查看是否连接
> 

> **真连接**：VPS像谷歌发送一条请求
> 

# 4、X-UI面板

<aside>
💡 纯粹的代码Linux不利于节点的操作和管理，所以我们可以从[X-ui官网](https://github.com/vaxilu/x-ui)下载X-ui面板作为管理的图形化界面，后期登录可以在浏览器上通过：
IP:端口 
域名:buzz:端口 
的方式登录

</aside>
