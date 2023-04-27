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
    
    ![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F1fca0d64-0101-4a0a-b1de-265672f82e67%2FUntitled.png?id=0c7e562c-75f3-40d6-9430-128710b49bdc&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)
    
    ![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ff24e3e99-2b39-4dbe-a4ae-1d3abd93ccb9%2FUntitled.png?id=db3ae125-65de-4fb8-b05c-bf0be615f372&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)
    
    > 本文的介绍基于**Ubuntu**操作系统，后期会加上**X-UI**
    > 
    

# 2、配置

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F2eb4ac86-fd89-474f-bf06-a59e4327e5ae%2F%25E5%25B1%258F%25E5%25B9%2595%25E6%2588%25AA%25E5%259B%25BE_2023-01-19_222836.jpg?id=c4afefc0-acd3-4f6b-bf2f-98623ba5cdd3&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

> 在SSH工具上配置好购买的VPS的IP和用户名（通常为root）、密码
> 

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fa9659147-0654-42c0-a3a3-812784a24f77%2FUntitled.png?id=79ea38cf-2de2-4db8-94cf-d36aac64d36c&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1030&userId=&cache=v2)

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F1973e81b-b9e3-4359-bd28-3604b0ac76d8%2FUntitled.png?id=4d1b84d3-83df-43c4-8170-5f4676a9c81f&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

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
