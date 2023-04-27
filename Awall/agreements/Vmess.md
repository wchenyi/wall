# Vmess

<aside>
💡       大多数人第一次接触到的结点的协议就是vmess（比如我），vmess协议不仅适配广泛，而且成本低廉，通用于免流。本质上和SS协议类似，都是将请求的数据加密为无序字符串，但是加密过程更加严谨，vmess协议比较依赖系统时间，如果更改系统时间就不能正常使用。

</aside>

# 1、加密原理

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F0d2895e4-6b63-4183-aae0-c7b38d5656c8%2FUntitled.png?id=daca0229-041d-499e-a6d5-735fa8195ec3&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

> 由加密方式和密钥确定第一次加密，使用时间戳和用户ID声称md5加密头，这是第二次加密
> 

## 1.1、淘汰原因

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F703d617b-217f-40a5-ac4d-1e3c090ba025%2FUntitled.png?id=fc3227f1-b270-4cf8-9914-3b83cb1fd5cd&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

- 因为在短时间之内头部可以重复适用，而且不适用AEAD加密方式，也就是说这个数据包可以被重放攻击
- 所以要想中间的数据包不被篡改，就需要对中间的数据包采用AEAD加密方式，那么头部的md5随机字符串就舍弃了
- 经过这种操作后，无法向下兼容，所以从版本v4.28.1之后设置为额外id为0就是AEAD加密方式，不是0就是md5
- 最终再2022.1.1彻底废弃了md5的加密方式，vmess和ss都是将内容加密为无规则的字符串，只不过更加的严密一点
- **所以之后额外id给0就好了，协议强制开启AEAD**

---

# 2、引入TLS

<aside>
💡 既然单纯的vmess协议存在缺陷，那只要像Trojan一样引入TLS变成http流量就行了

</aside>

- 仅仅是建立好一个AEAD加密方式的vmess节点本质上还是一个无规则的字节流
- 需要和Trojan一样，引入TLS来使得其成为一个正常的https数据流

**加密方式：**

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F8c321a41-a47e-4de8-8365-f0bcc00e2e92%2FUntitled.png?id=38126f8e-10f9-4009-a03b-76d49ce9a0b3&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

# 3、最原始的Vmess（Vmess+TCP）

## 3.1、Vmess+TCP+TLS

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F0ab69cfc-c258-47c1-bca6-c4dec46df280%2FUntitled.png?id=38b91570-12fc-4486-a7ed-106656ae9557&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

> TLS的作用就是，给数据流加上一个http头部伪装成一个正常的http流量
> 

## 3.2、承载

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F6f31fa0a-0696-4182-b787-7468139e4ef6%2FUntitled.png?id=97f2abf8-96bd-41df-910f-994fd3e1a840&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fc36e97cd-ecf1-49a9-8a7a-085b54548546%2FUntitled.png?id=5c5c6e24-c375-416a-ad15-0f553e5c99e1&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

> 改为TLS之后，将TLS放在和vmess平级的地方，并由其承担vmess发出的流量，再转给TCP
> 

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fec48bb53-7377-4aec-9343-c352fb189115%2FUntitled.png?id=6213c80b-1ff6-4c9a-86e0-94965fba5ae1&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

**协议：**

- **TCP**：需要先建立连接的一种协议；
    - **ws**基于tcp，ws承载vmess，tcp承载ws
- **UDP**：不需要预先建立连接，只管发不管你到了没有
    - **kcp**基于UDP的

## 3.3、伪装

- 伪装在vmess前面加上一个http头部，伪装成http流量
- 但是本身不是由http承载，还是由tcp/udp承载（ws没有伪装）
- 伪装也常被用于[伪装免流](https://wangcy.cf/be090a08bd974053b304d4dbad81e1b6)

# 4、协议嵌套

## 4.1、Vmess+ws+TLS

- Vmess流量给ws，ws流量给tls，tls流量给tcp
- Tcp或者ws优先选择，传输层只有TCP和UDP

## 4.2、Vmess+TLS+TCP

- Vmess的流量由tls承载，tls的流量由tcp承载
- 这种情况下无法再认证失败后跳转到正常网站来回避GFW审查

## 4.3、Vmess+ws+TLS+web

- 因为vmess不能像Trojan一样在认证失败后跳转到一个正常的网页，所以如果这个时候GFW来审查就可能出问题
- 解决办法就是在原本的vmess+tls+tcp的基础上增加一个正常的网页来作为认证失败的时候的跳转
    - 这个网页可以由nginx来代理到一个别人的网站
    - 或者是自己的其它网站
    - 再或者是专门在服务器搭建一个伪装网址
- Tcp不能直接做到，所以要改成ws（客户端和服务器都要改）
- 和Trojan的不同
    - Trojan中是由Trojan直接处理外部的流量
    - 而这种方案只有nginx暴露在外面，可以更好隐藏vmess服务器
    - 监听只允许本机，不是0.0.0.0，因为是本机直接对nginx负责
    
    ![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fbd319272-1d6d-462b-bc0c-859843a568df%2FUntitled.png?id=c010abb6-fbff-41f6-b57b-bc5d163ab376&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)
    
    ![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F7e96f1fb-26cc-4a51-9b0b-3593831009a1%2FUntitled.png?id=7364e2ef-89c4-44e4-88bf-558d8747575c&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)
    

## 4.4、nginx

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fb76ad49d-7d47-41b2-bfc7-afffe2907bcb%2FUntitled.png?id=2aa5cf9d-9612-4442-ad08-0cf41428f2b4&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

> 如果是tcp协议经过解密后就是vmess的部分，nginx无法解析vmess，只能由ws进行二次封装
>
