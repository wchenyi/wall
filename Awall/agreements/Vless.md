# Vless

<aside>
💡 是一种轻量的vmess，vmess还存在二次tls加密的问题，解密需要的时间过长，Vless可以去掉tls的二次加密，速度更快，同时适配的客户端最多，被广泛使用

</aside>

# 1、关系

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F1e046b00-2fe0-43bd-b5f3-6f6612499834%2FUntitled.png?id=420a5620-7e33-41ae-9e8c-507fba38d10e&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

- Vless是RPRX开发的协议，但是他作为v2ray的主要开发者之一
    - 目的是为了解决vmess历史遗留的过于臃肿的问题
    - 之后开发了xtls，刚出来不想被滥用所以在开源中只限于编译（v2ray分家）
    - 后面的人无法基于此进行打包，X说你想打包就打包吧，我只是这么写
    - 后面说x不改就停止对v2ray的支持，x不懂debian/Ubuntu的规则，事先不知道v2已经被打包，x是win用户，对于linux只限于服务器，说大家都是用命令安装的，跟debian的沟通产生误会后解释不清，炸毛了情绪化发言被围攻
    - V2的另一个主要开发者说愿意修改协议，而这产生分歧，他表示愿意遵循开源协议，提供一个脚本来移除xtls的代码
    - X先生则是另立门户，基于v2ray发展自己的xtls开发xray，功能和v2ray差不多，但是支持xtls
- 和Trojan本质都是不对数据进行加密，交给tls进行加密，只是头部没有Trojan（56）长，因为只有uuid（16）

# 2、vless

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F94ca2ae1-546f-4695-ac77-847f12651e96%2FUntitled.png?id=5b0452bf-dde5-4c88-9542-2e85cfedfb9e&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

# 3、回落

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F9cde0cd7-ed66-4a2c-ace5-1895b3e9c384%2FUntitled.png?id=8d1851c8-736d-4bda-acce-2a62f80c8b73&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

> Tls1.2 的序列号相当于1.3比较有规律，容易被GFW捕捉到，xtls已经被精准的探测到了
> 

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F9cde0cd7-ed66-4a2c-ace5-1895b3e9c384%2FUntitled.png?id=8d1851c8-736d-4bda-acce-2a62f80c8b73&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

> 在**Trojan**中，对于不符合的流量会落到上一步，继续寻找符合的，可以公用一个端口，一个端口可以搭建不同的协议，只有vless能用
>
