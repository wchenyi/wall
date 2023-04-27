# 线路、CDN

<aside>
💡 经由“互联网”这一节我们已经明白互联网数据传输的基本流程，接下来为了解决搭建好的节点的速度问题，我们要对已有的线路进行优化以实现“走最短的路”

</aside>

# 1、线路-CDN

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F8483d857-64d9-4207-adde-0182e6cb8945%2FUntitled.png?id=0fbd6218-18af-45f5-a469-736cf8f88079&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1120&userId=&cache=v2)

- 因为要跳跳跳所以需要优化线路
- 在这里直接安装X-ui图形化操作页面（记住ufw disable）
    - 适用ip:端口的方式在浏览器地址栏进行登录，设置最新的xray内核
- 引入CDN的概念（内容分布网络）
    - CDN本身就相当于我们要访问的目标服务器
    - 当我们向目标服务器发送请求时，会就近到CDN，CDN检查自己的缓存列表是否有需要的内容，没有则找上级CDN（之间使用专线连接）
    - CDN绕开了拥堵的网络（网络加速），还可以缓存得到的内容（内容分发）
- 如果套国内的CDN就要实名制备案，国内CDN被封死了
- 套国外CDN（cloudflare）很堵】
- **CDN类似于中转，但是只能转发特定端口和ip的流量，只能是http协议的流量，也就是ws**

# 2、CloudFlare

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F3c984d4d-0f6a-43da-bf9c-dd70f0dee586%2FUntitled.png?id=26334370-3771-4f96-b5b1-c172e412c1c6&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F3c984d4d-0f6a-43da-bf9c-dd70f0dee586%2FUntitled.png?id=26334370-3771-4f96-b5b1-c172e412c1c6&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

> IPv4就是自己的vps地址，没开代理就是没套CDN
开了之后就已经套用了，测试ping不是自己的vpsip是正常的
> 

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F85a3ae90-635b-4e40-b8b0-15a9b41300df%2FUntitled.png?id=78d65a0e-b541-4a64-8ac2-357a5b0fa28f&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

# 3、CDN的作用

- CDN可以充当反向代理的作用
- 即使你的服务器ip被强了，那你只要有一个没有被墙的CDN，CDN会转发你的流量
- 如果你的CDN被墙了，那你只需要拿掉CDN或者换一个CDN
- 如果使用的CDN效果不是很好，可以自己更换CDN
    - 首先找到[CF的全部CDNIP](https://www.cloudflare.com/zh-cn/ips/)
    - 然后对找到的IP进行[cidr计算器](https://www.sioe.cn/xinqing/CIDR.php)进行计算，测试ip段中的ping是否可以连接，如果都不通可以用ping.pe进行查看
- CDNIP太多，可以使用[优选IP](https://www.sioe.cn/xinqing/CIDR.php)
    - 原理：先ping出能用的，按照延迟排序，从一个地方下载（取决于本地网速）
    - 另外网络是有抖动的，所以当时测得不一定就是现在测的，还有GFW的针对

# 4、修改CDN

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F2ffd7c70-d9b0-404d-a477-86e82f8f3797%2FUntitled.png?id=5eb1ac7a-8ce5-4999-a755-459c58d54de5&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)
