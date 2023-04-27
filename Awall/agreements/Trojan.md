# Trojan

# 1、概述

- 通过SS协议我们可以知道，单纯的对本地请求的域名内容进行伪装经过GFW是十分不安全的。所以需要Plugin插件，为伪装的内容加上http请求头来冒充http流量。由于互联网上一半左右的流量都是http流量，所以伪装成http流量是十分“保险”的，这也是本节**Trojan协议**的特色。

- **Trojan协议**是将端口监听到的流量变成http流量，可以简单地理解为加了**plugin插件**的SS协议，不同的是Trojan协议本身就是一个拥有正规合法的域名证书的TLS协议（这部分后文再解释），就算是GFW进行重放攻击，Trojan协议也能够将GFW的访问介入一个正常的网页（这个网页可以是自己做的假网页，也可以是一个正常的网页，比如baidu.com）；这就很大程度上规避了GFW的审查。

- 当然也存在着一些缺点，比如双层TLS加密等，但这不是Trojan协议存在的问题，而是所有伪装成http流量的协议或多或少都会存在的问题。这会降低解码效率，延迟增加，但是也有相应的解决方案。总的来说这是一个比较成熟的协议，不仅有着覆盖全平台的客户端的支持，而且有着很多人对这个协议进行完善改良；该协议也被广泛的应用在一些专线、解锁流媒体等节点中。值得注意的是，该协议对免流不太友好。

---

# 2、辅助知识

<aside>
💡      在介绍Trojan协议之前，首先需要引进**http协议**、**https协议**和**TLS、域名、证书**等概念。这些内容既是了解翻墙必不可少的概念，也是整个互联网中关键的部分。

</aside>

## 2.1、HTTP

- HTTP协议即“明文传输”协议。超文本传输协议（Hyper Text Transfer Protocol，*HTTP*）是一个简单的请求-响应协议，它通常运行在TCP之上。我们常见的在浏览器地址栏中的以`http://` 开头的部分就是http协议；是现存互联网上最大的协议。

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ffd8099d2-ee44-414f-a530-7b94950b55f7%2FUntitled.png?id=2e114806-0805-4928-b890-b3425a37f882&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

- 其传输过程是将HTML（Hyper Text Markup Language），即超文本标记语言通过浏览器加以汇编后明文进行传输的协议。其优点是覆盖全平台，效率极高；缺点是过程是明文的，输入的任何内容都会被中间经过的服务器看见或者更改。**例如：**

请输入账号密码
账号：123
密码：456

**经过中间服务器乃至于防火墙的时候显示的就是:**

```html
<!DOCTYPE html>
<html>
	<head lang="zh">请输入账号密码</head>
	<body>
		<p>账号：123</p>
		<p>密码：456</p>
	</body>
</html>
```

- 这在当今社会是极为不安全的，所以现在的浏览器地址栏的网址一般是`https://`开头的，http后面的s就是TLS非对称加密协议，纯粹的http://开头的网址已经被大部分浏览器认为是不安全的并弹出警告。

---

## 2.2、HTTPS

- TLS加密协议是一种非对称加密算法，通过TLS对http进行加密后的数据只用通过特定的公钥才能够解开。而公钥是记录在CA证书上的，CA证书由权威的认证机构颁发，我们的计算器将这些权威的CA证书颁发机构添加的本机的根证书目录，作为信任的标志。一但是这些机构颁发的证书就会被互联网所承认。

      `HTTPS=HTTP+TL**S**`

- **对称加密**：ss——加密的密码和解密的密码保持一致（123-123）
- **非对称加密**：公私钥（私加123，公解321）
私钥自己生成，公钥是基于私钥生成出来的
公钥公开，任何人都可以知道，私钥保存在自己的服务器里

- 所以要想进行TLS加密首先要有证书，证书要在CA机构申请（有特定的代码，详见[VPS节](https://wangcy.cf/4-VPS-40f07ff75fb040de8f5539ccdccc1688)），申请证书之前需要有一个域名（详见[域名节](https://wangcy.cf/d37ad63ebe5140938ea5c5601aa7e808)）以及其公钥和私钥

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fa864add1-ca59-4f2f-bcba-f4ff0d74a816%2FUntitled.png?id=b3bb0c83-dd6e-44e5-ad30-dcb298d687be&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

> 申请证书的过程你可以想象成是逆向CA证书颁发机构提出申请，CA机构需要你证明你的域名是你的（*比如让你在你的域名网站上加上特定字符等*）
> 

---

## 2.3、TLS加密

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F90ba457c-59fd-4698-8aef-fff63d3b38d0%2FUntitled.png?id=348bb15d-2664-446a-9c89-463b5296969d&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

- TLS是浏览器自行对于浏览器发送的内容进行加密，这部分在经过任何中间服务器乃至于防火墙的时候都不是明文状态
    - 当然也不是绝对的安全，抓包软件已经识别了CA证书的加解密方式并提供了证书破解
    - 但是现阶段还是相对安全的，涉及到账号密码等安全内容会有其他加密方式
- 只加密你的传输内容，而不是对于所有的域名、IP、端口等都加密
- 不需要对网站进行加密，因为一个IP可能有多个网站，每个网站都有自己的公钥和私钥，网址sni
- TLS1.3可以加密sni——esni——GFW直接丢包（你可能借机访问被禁止的网站），这种方式还没有普及，如果普及GFW也要做出相应的修改

---

# 3、Trojan

## 3.1、证书

- Trojan因为是模拟https所以需要申请证书，所以需要域名
    - 可以自己购买也可以自签
- 放上要申请的域名，独立安装的方式
    
    ![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fe31c7cb5-c3c3-4b17-850f-7d6f9a328755%2FUntitled.png?id=245e3b0f-2004-4dd2-a76d-bf262799762f&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)
    
- 得到的私钥和ca证书链安装

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fad67d545-b255-48f9-94be-90ec244ee1b8%2FUntitled.png?id=223e9379-730c-45fe-8d95-2644b83a9ba9&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fef5c5147-b67f-449d-a43f-3f286c3bb957%2FUntitled.png?id=03354d7e-b56d-46c2-b191-bf9f6b211048&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1410&userId=&cache=v2)

- 如果是自签就写上vps的ip，如果是购买域名可以直接写域名，sni默认不写
- 自签就是自己做CA，这种需要不严重或者添加到受信任的根证书certmgr.msc里面

---

## 3.2、流量传输过程

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F62c51202-519b-456d-b465-73a3fd5527f6%2FUntitled.png?id=1622d260-db07-43c6-84ae-b2a98ad8b829&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

> Trojan协议实际上是经过了2此TLS加密
> 
- 第一次是https自己本身的浏览器加密，第二次是Trojan协议的加密
    - 前者加密请求内容，后者加密请求域名，后者的加密覆盖前者
- Trojan是正经的申请合法的域名和证书，所以在经过GFW的时候不会因此怀疑，因为和plugin插件伪装的http流量不同，Trojan本身就是合法的http流量
    - 如果使用的不是CA证书申请，而是自签的话；需要将自己的自签证书加入需要进行访问的计算机的根证书目录或者不开启证书验证
    - 同样的，这会伴随安全风险和GFW审查的风险
- 就算GFW对Trojan服务器释放重放攻击，Trojan自身的域名在配置完成后也可以将不通过验证的访问导向一个正常的网站（比如baidu.com）

---

## 3.3、效果

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fb9bd95d5-e30a-4fb7-a01e-c03030dbefcf%2FUntitled.png?id=d00cf913-0cc1-4cb5-944c-682a33ad614c&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

# 4、存在的问题和解决办法

<aside>
💡       Trojan也有自己的问题会进行两次的tls加密，第一次是自己的加密，第二次是正常访问目标的tls加密，目的都是为了伪装成https流量，其他的方法或多或少也会存在问题。可以通过XTLS的方式进行解决。

</aside>

## 4.1、XTLS

- XTLS是X先生写的一个协议，目的是解决因Trojan协议带来的TLS双层加密的问题，通过精准的探测双层TLS的特征，抹除重复加密的部分来缩短解密的时间，使得Trojan的性能对大化。

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fb9bd95d5-e30a-4fb7-a01e-c03030dbefcf%2FUntitled.png?id=d00cf913-0cc1-4cb5-944c-682a33ad614c&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

> 本质上消除两次加密重复且不需要的部分，减少加解密时间，性能接近于裸奔
> 
- 本机在浏览器发送请求，首先被浏览器的http加密一次，但是目标域名之类的因为要向DNS获得IP，所以没有被加密。而IP例如google.com如果直接发送会被GFW的黑名单识别拦截
- 所以再经过Trojan协议的二次TLS加密，这个过程隐藏了原来http://的内容，在前面加上了Trojan协议的域名伪装成正常的http流量。目的是为了隐藏本机的域名请求意图
- Trojan的内容加密部分就是第一次在浏览器搜索的部分，Trojan的服务器IP不再GFW的黑名单之中，且域名的证书是合法有效的，所以不用加密Trojan的域名请求

---

## 4.2、趣闻

<aside>
💡 有很多人好奇X-ray和XTLS的关系，实际上没啥好说的，就是几个误会交织在一起发展出更大的误会

</aside>

- XTLS的开发者X先生在开发XTLS的时候是v2ray的主要开发者之一，并在v2中引入了XTLS的代码，因为怕XTLS滥用所以在GitHub的开源文档中写了目前只做汇编之类的。Debian系统开发者给X先生留言说希望更改开源内容，以便可以在Debian中打包。

 - X先生回复说我虽然是那么写的，但是你想打包就打包吧；但是Debian认为你的开源报告中的说法不符合开源打包的要求，所以坚持希望X先生修改，否则就只能下架。这个时候X先生不知道自己的XTLS已经被打包进了Debian，而且X先生主力机是Windows，在Linux中也主要是用命令安装东西，所以对Linux开源社区的规则不太了解（可能还有X先生和Debian的交流都是用的谷歌翻译的锅>_<），所以X先生就是倔强的不改

- 然后v2的另一个主要开发者出来当和事佬，说会出一个脚本来删除v2中XTLS的代码，然后X先生就炸毛了。就离开v2ray出来单干，开发了自己的[Xray](https://xtls.github.io/)，他的书名文档写的很有意思，几乎是白话文，大家[可以看看](https://p4gefau1t.github.io/trojan-go/basic/trojan/)。

- X-ray就一个内核，v2ray这个软件是运行内核的图形化界面
