![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ff16df5c3-d8ca-4ebf-b67b-43dc9c3993a2%2Fgfw.png?table=block&id=dfbe96c3-e92c-4223-80b7-b75b54748e45&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

# GFW的原理

# 1、翻墙的大致介绍

## 1.1 墙的大致介绍

- **GFW**全称“**Great Fire Wall**”，即长城防火墙，主要包含“互联网审查”和“国际访问阻断”两种功能，前者是互联网都有的特征，在国内的网站也需要经过审查，对其内容、发布信息等的审查；后者是对于访问国家禁止访问的国际互联网内容进行阻断的内容；这里的观点不是从网上直接复制粘贴的，而是基于我自己的了解自行总结的

- GFW的初衷是好的，建国初期国外敌对势力通过互联网的方式对我国进行多次不正当的妨害，企图颠覆我国政权，侵害我国的人民；国家要求推特、脸书等国外互联网巨头提供这些人的信息遭到拒绝，诚然它们如果为我国开这个先例的话也会被其他国家的政府要求公开，所以在各方利益考量下，我国政府选择封闭国际互联网的举动也是极其正确的；鉴于当时我国的互联网技术还不够成熟对于这些恶意的内容很难做到针对性识别，故此只能进行一刀切来保证我国的发展和社会主义建设

- **[参考文献](https://gfw.report/blog/gfw_shadowsocks/zh.html)**

## 1.2 翻墙的现实需要

- 由于我国正值发展阶段，必要的对外贸易和交流往来是难以避免的，所以一刀切的方式难免利弊难以均衡考量，所以在此基础上国家进行了两种措施，一种是完善GFW的运行拦截机制；另一种是对确有必要进行国际交流的跨国公司、留学生等个人和组织由工信部发放许可，经由国家许可的营业厅、信道、端口等访问需要的国际信息

- 然而随着社会的发展，我国同国际的交往越来越密切，GFW的审查机制又比较“死板”，一些个人和组织对国际上开展的合法信息交流受到了不可避免的限制，例如学术工作者需要访问谷歌学术来进行学术研究，计算机学习和从业人员需要通过GitHub、GitLab等获取资料信息；然而工信部的许可门槛相对较高，三家营业厅的套餐对于一般个人而言费用过高

## 1.3 普遍误区

- 首先需要说明的一点是，翻墙并非自己搭建了一条违法的“**国际互联网信道**”，而是使用国家已经搭建好的“信道”，可能在目的和手段上会存在不法行为，但是物理线路本身是国家许可的。

- 很多人认为翻墙是一个比较小众的群体，这里我也不好过多说明，根据博主“**电丸科技AK**”从2019年数据来看访问谷歌的有3000多万人，算上其他的内容假定有5000万人，2019年网民人数截至12达6.88亿约等于7亿，那么翻墙的人数保守估计占比1/14；2019年后新冠疫情爆发，人们对网络的要求持续上涨，由于一些敏感原因国内翻墙人数也在上涨

- 经过“**N号房**”事件后，翻墙为公众所大范围知悉，但是大多数人停留在翻墙只是为了**黄色、暗网**等违法犯罪的需要，这是很片面的观点；本人不排除一部份人确实是这样，但是我们应当从更俯瞰等角度来看待，可以把虚拟的防火墙想象成现实中的围墙，在墙外获取的服务和国内过去的服务在性质上是没有区别的，无非就是音视频、新闻、搜索等，就像“**谷歌-百度、推特-微博、油管-b站（这里只是简单类比）、电报-微信等**”

- 既然国内外的性质一样，那么为什么还要特地翻出去看外边的？这是因为虽然性质一样，但是内容却大不相同，拿百度举例，百度充斥着广告和搜索等不相关内容，谷歌，就不会资源还更多；同样的软件例如WPS，国外版本就会体积更小，功能齐全，广告和对个人信息的索取更少等优点；在这几点上，国外的互联网发展的要更早，相关的规范也更加的健全。除此之外流量上也有很大的差异，油管每个月都有几亿人次的访问量，涉及的方面也要更多；微博和推特相比，由于我国人口基数大，微博的人数会更多，但是在质量上微博更偏娱乐，排名前几的也是明星，而推特排名前几的是明星和一些总统

- 总之在性质和类型上国际互联网包括中国互联网，翻墙只是扩大了获取互联网信息获取的量，并不绝对的导致犯罪和不法行为，就算是在国内也有不发的因素在传播，仅仅将墙作为检验人心的标准，就是对自我文化的不信任；秉持一颗明亮的心，提高辨识能力才是最重要的。

- 最后笔者在这里问大家一个问题，为什么不能翻墙？如果说墙是国家政治考虑，那么就是国家对于本国人的规范。我们在成为一个国家公民之前，首先我们是一个人，那就拥有自由，人可以到敌对国家去，可以改变或增减自己的国籍，但是他能改变作为一个“人”的事实吗？人有创造一切的权利，也有到任何地方的权利，这不是你能不能，而是你有没有资格。我们从小到大真的是别人不让做什么就真的不去做？何谓对错，只不过是一个判断，做是你的资格，因此得到的后果是你的责任。

# 2、墙的运作方式

- 翻墙是用技术手段突破GFW的封锁，为此我们首先要搞清楚没有GFW的时候互联网是怎样运行的，然后再搞清楚GFW是怎样对这个过程进行阻碍的，内容参考自油管博主“电丸科技AK”

## 2.1  没有墙的情况下

**本地PC➡️**本地互联网出口**➡️**骨干网**➡️**DNS域名解析器**➡️目标服务器➡️**（同样的流程返回）**本地PC**

![](https://pomf2.lain.la/f/11wjhdpk.jpg)

**术语解释**

- **本地PC**：本地终端设备，手机、平板、电脑等，用于发送你的信息请求
- **本地互联网出口**：不严谨解释的说可以认为是这一片区域一个对很多用户总的管理
- **骨干网**：用来连接多个区域或地区的高速网络，我国一共有9个，拥有国际互联网访问权限
- **DNS域名解析器**：*Domain Name System*，将输入的如http网址找到对应的IP地址
- **目标服务器**：即你想访问的网址服务器，如谷歌、百度等，得到的数据再原路返回你的本地PC

## 2.2 墙的运作方式

- 由于骨干网已经有访问国际互联网的权限，所以GFW只能在这之前截获你的信息请求，通过污染你的DNS、检索国家禁止访问的关键字以及端口阻断的方式来阻止你和想要访问的目标服务器进行通信

**本地PC➡️**本地互联网出口**➡️**骨干网**➡️GFW进行审查是否传输给DNS服务器**

![](https://pomf2.lain.la/f/p76h1ww.jpg)

**术语解释**

- **DNS污染**：根据请求的域名得知访问的服务器是被禁止的，于是进行阻断后返回一个错误的IP
- **过滤关键字**：如果无法根据域名来得知访问的服务器是否被禁止，就看你的请求包里有无国家收录的敏感文字内容，如果有进行阻断后返回一个错误的IP
- **端口阻断**：不严谨地说不通过上面的方式，直接通过端口阻止你访问任何这信息，如443端口

# 2、墙的阻断结果

![](https://pomf2.lain.la/f/2xen9wj.png)

> GFW有五层结构，这就意味着GFW能够完整的解析到我们的意图，当他认我们的目标意图存在于自己的**ip地址黑名单**或者**域名黑名单**时，就会阻断，具体来说会出现以下几种情况：
> 
- GFW判断你所请求的ip存在于黑名单中，所以不能给👉篡改本来获取到的真实IP——**DNS污染**
- 通过修改hosts文件获得真实IP进行访问，但GFW的IP/域名黑名单中有你所请求的IP👉干掉/作假真实IP——**TCP重置攻击**
- 通过修改hosts文件的方式建立了连接，且此IP不存在于GFW的黑名单中，但GFW解析发现你访问的域名不干净👉**干掉**
- 通过VPS/VPN，GFW解析发现在黑名单域名👉**干掉+封锁**VPS的IP
