# Shadowsocks

<aside>
💡 不同于VPN，这是一种翻墙而生的协议（虽然作者好像被请去喝茶了，也有同名软件），简称SS，是一种借助于本地客户端对GFW最终解析到的域名请求做出对称加密的方式加密域名请求来逃避GFW的审查，真正实现了既能加密流量，又没有流量特征

</aside>

# 1、原理解释

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F38eeac5c-569f-4bd0-932a-257385c0aebd%2FUntitled.png?id=b79323ce-0e7e-4f1c-9285-182308e7f716&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1380&userId=&cache=v2)

1. 首先在本地客户端（例如v2ray）设置好需要监听的端口
2. 浏览器发送的数据会优先被SS客户端监听
3. SS客户端对所监听到的内容进行加密

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F059a66aa-ed79-4f05-8f5f-70cb8c5cf196%2FUntitled.png?id=2ab3980d-035f-44ed-bae7-786b679c3174&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1260&userId=&cache=v2)

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F1ed633c6-fbc1-41ae-8aa0-de5c735112e8%2FUntitled.png?id=d60b7a5b-57bc-4737-87ff-62c687867b44&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1080&userId=&cache=v2)

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F337bbbd9-9bc6-4a6c-b5e8-64d60e506209%2FUntitled.png?id=876bdce4-2779-4ed9-ba95-a2cfc7272cc8&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1250&userId=&cache=v2)

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F9ee2fbc7-8109-4971-bcf6-aa6c6a08b1cb%2FUntitled.png?id=1eb11b58-6425-404f-b19a-40c2b2b90e8f&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

> 本地客户端将监听的内容使用**对称加密（加密和解密的密钥相同）**的方式对请求的域名（例如：google.com）加密成无序字符串，并配置好VPS的地址和端口
这串被加密过的数据流经过GFW时，因为无法解密加密内容因而无法得知请求的域名内容，只能获取要访问的VPS服务器，所以放行数据
> 

# 2、优点

- 不同与使用VPN进行翻墙的方式，此协议转为翻墙而生
- 双层服务器加解密（本地软件例如v2ray和墙外的VPS服务器）
- 虽然不如VPN代理的级别高，部分系统级别的应用无法即使开全局也无法代理，但是翻墙比较稳定而且成本极低
- 对于局域网共享、伪装域名混淆免流等自定义功能的支持比较完善
- 开放程度较高，各类教程比较完备，可以多样化的阻挡GFW的审查

# 3、问题

## 3.1、重放攻击

<aside>
💡        虽然SS是一个非常好的协议，开创了翻墙的新起点，但是现在使用实际上已经很少了，原因在于GFW可以主动向国外的VPS服务器通过重放攻击进行审查，如果SS的协议设置不够完善，GFW就会发现其运行有SS协议并将VPS的服务器列入黑名单，这样这个节点和这台VPS就基本上废了

</aside>

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F795fbe0b-c6c0-4350-8e51-ce758f6f47ac%2FUntitled.png?id=3a6a02c8-a262-4cc8-b115-ce62d661c782&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

- **本地发送流量**：ss将流量加密，在经过GFW的时候，GFW并不知道我们想要访问的域名内容，且SS服务器的IP并不在GFW的黑名单中
    - GFW或许会认为你可疑，但互联网很大，GFW也不能保证所有自己的数据库没有记载的IP都有问题，所以GFW只能放行
- **经过GFW**：然而数据流是要发送给SS服务器的，所以要配置好SS服务器的IP和端口等内容，且这部分信息经过GFW时能够被GFW所探知
    - GFW通过探知的内容捏造一个数据包发往SS服务器
    - GFW虽然能够获得IP和端口但是无法获得SS加密本地数据的密钥
    - 因此SS服务器对GFW发送的数据包密钥验证不通过并给出错误回执
- **结果**：GFW虽然无法和SS服务器建立有效链接，但是GFW却可以通过这个举动判断SS服务器是否运行了SS协议，从而对SS服务器做出IP封锁

> **此种攻击方式被称为重放攻击，如果你是SS服务器的持有者，你可以通过命令查看SS协议运行状况，找出不属于自己本地发往SS服务器的IP的失败链接，通过[Ping](https://tools.ipip.net/traceroute.php)的方式找到该IP的归属地**
> 

## 3.2、预防措施——plugin插件

<aside>
💡 插件的目的在于伪装流量，将SS协议所代理的流量伪装成一个正常的http或者websocks流量，具体的分类有v2ray plugin等

</aside>

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F406d1963-3e2b-43c8-a777-d91cfe386d76%2FUntitled.png?id=944c371b-3075-4537-b32c-e09866da2ef6&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

- **http协议头**：在已经加密好的**SS协议**前面加上一个http协议头，将任何流量都伪装成一个http数据
- **GFW处**：在这部分**http协议头**能够被正常看到，但是**SS协议**部分却仍处于加密状态
- **VPS部分**：加了插件后数据包经由**GFW**发往**plugin插件**，而不是直接发送给**ss服务器** ，由**plugin插件**的监听端口，去掉**http协议头**，把真正的内容还原发往**ss节点服务器**

---

但要注意的是并不是所有的客户端都支持plugin插件功能

## 3.3、混淆等解决方案

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fb8f6668d-77cc-4cba-be32-dd08aeb0e335%2FUntitled.png?id=715096f4-eec5-4f84-8ec8-c91d4539e395&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fa1fa7e17-b934-4327-bbd5-7606ce925a03%2FUntitled.png?id=5be029e0-6491-4667-8073-c60e730d5adf&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

> 近些年来不加插件直接裸奔SS协议就是找死，也可以通过CDN（详见线路节）或者更换SS服务器IP的方式救急，通过AEAD等方式加密比较常用
>
