# VPN

<aside>
💡 VPN（Virtual Private Network），虚拟专用网络，目的是为了联通两个内网，并起到加密作用，并不是为了翻墙而生，但是其流量特征可以被用来翻墙，使用时间较早，因此被民间认为VPN就是翻墙的代名词

</aside>

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fc06a6559-d35f-4134-9584-6dbfa7bb4871%2FUntitled.png?id=e3c46613-9395-4c3e-a896-01daea51939b&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1470&userId=&cache=v2)

- VPN数据加密，IPSec OpenVPN——特征明显
- 但是由于VPN本质是用来合并两个企业的内网的，所以GFW不会直接干掉
当特殊时期、长时间大流量连接就会被中断

![](https://wangcy.cf/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F0e9de951-760b-48c8-b2d1-1749b2f2a4b2%2FUntitled.png?id=17b1cb68-9547-44c3-9da6-0fb8a8ca0c8d&table=block&spaceId=05a1b89d-ff84-4035-bdc6-863a0fae0b47&width=1530&userId=&cache=v2)

> 和VPS不同的是，VPN是直接将内容经过GFW发到目标VPN服务器，并借由VPN服务器转交真正的意图
> 
- 优点是相较于代理，本地可以没有客户端直接通过网页进行，以及代理层级较高，可以最大限度地代理系统级应用
- 缺点是在本地不进行客户端的伪装加密，直接经过GFW告诉GFW本身VPN服务器，GFW服务器对VPN的IP敏感，容易封锁或者是在特殊时期封锁

<aside>
⚙        综合来说这种方式已经不再推荐，VPN本身在公司之间作为内网联通的手段应用广泛，且在国家备案。例如学校内部校园网从外部访问的时、知网在校外访问时的VPN线路等。然而作为翻墙来说，流量未经混淆或加密经过GFW就会被记录下VPN的IP地址，这有利于GFW对VPN服务器的活动进行监视。
       现在活下来的VPN除了钓鱼型的VPN之外，剩下的VPN要么是手里有着能够和GFW相抗衡的IP数量的境外VPN服务，这种或许质量不错但是收费极其昂贵；或者是套壳机场代理节点的VPN。若是想要稳定的翻墙还是均衡考虑这种方法。

</aside>
