<!-- logo -->
<p align="center">
    <a href="https://wangcy.tk" alt="Wangcy Logo">
    <img src="https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F9896bb2e-d7f9-41ac-a4e6-5f9ac2d2f652%2FWCY%E7%9A%84%E4%B8%AA%E4%BA%BAlogo.png?table=block&id=e714d3e8-f158-486c-87e0-baa42b87f805" height="173"/></a>
</p>

<!--个人项目跳转页-->
<div align="center">
    <a href="https://wangcy.tk">主页</a> |
    <a href="https://blog.wangcy.cf/">博客</a> |
    <a href="https://wangcy.tk/wall">Awall</a> <br>
    <a href="https://ycu.wangcy.cf">YCU起始页</a> |
    <a href="https://sou.wangcy.tk">简约起始页</a> |
    <a href="https://wangcy.tk/Wallpaper">壁纸</a> |
    <a href="https://donate.wangcy.tk">投喂</a> 
</div>

<!--语言标识-->
<br>
<p align="center">
    <img src="https://img.shields.io/badge/Language%20-HTML-blue">
    <img src="https://img.shields.io/badge/Language%20-MarkDown-green">
    <a href="https://github.com/pages-themes/cayman" ><img src="https://img.shields.io/badge/theme-Jekyll-red"></a>
</p>

<!--语言切换-->
<p align="center">
    <a href="https://wangcy.tk/wall/CHN"><img src="https://img.shields.io/badge/%E8%AF%AD%E8%A8%80-%E4%B8%AD%E6%96%87-brightgreen"></a>
    <a href="https://wangcy.tk/wall/Eng"><img src="https://img.shields.io/badge/Language-English-brightgreen"></a>
</p>    
    
# 目录
> [1.建站声明](#1%E5%BB%BA%E7%AB%99%E5%A3%B0%E6%98%8E)<br>
> [2.建站过程](#2%E5%BB%BA%E7%AB%99%E8%BF%87%E7%A8%8B)<br>
> [3.站点内容](#3%E7%AB%99%E7%82%B9%E5%86%85%E5%AE%B9)<br>
> [4.预览效果](#4%E9%A2%84%E8%A7%88%E6%95%88%E6%9E%9C)

# 1.建站声明

> 出于学习交流目的建立此站，与此无关的盈利行为和非法行为与作者无关。
> 本站作者既不希望也不提倡在未经相关组织许可或者为传播不当信息为目的使用本站所提供的工具和信息<br>

使用者请确保已经已经学习了有关于长城防火墙的产生原因和工作原理等网络安全知识和刑法网络安全罪名、行政法规对访问国外网站和自建国际互联网信道的有关知识。
如果对以上概念不熟悉或对自己的使用性质不能明确的禁止使用本站点提供的内容，如果从其他途径获得了与本站提供的服务相似或者能够达到相同目的的与本站无关。<br>

🤣这个项目就是我做着玩玩的，如果大佬看到了请高抬贵手，对我的不当行为做出指正。同好们看到了觉得有用、好玩的话就私下玩玩，不要当真，不要传播。

# 2.建站过程

1⃣️这个项目是我本人除了使用的Jekyll模板等内容完完全全用自己的知识开发的，虽然实现原理很简单，但还是很有成就感的。本片说明也是我第一次写README<br>
2⃣️本站以Jekyll的[Cayman](https://github.com/pages-themes/cayman)主题为基础，深度定制了本站主题，本站主题和本站内容深度绑定。并不适合其他人用作自己的*jekyll*主题，如需使用还请使用原版。在这里说出修改的部分，但请注意本人并非系统训练过的开发者，所以在专业词汇和内容上可能不够精确或者完全不对，请大佬们多多包涵。<br>
3⃣️这里所写明的是针对原版主题[Cayman](https://github.com/pages-themes/cayman)的个性化修改内容，为了便于修改，我删掉了原本的[README](https://github.com/pages-themes/cayman#readme)。重写了自己需要的修改部分，想要查看原文档的请去看原本的仓库。本主题只为本人的一个项目[Wall](https://wangct.tk/wall)做深度定制，所以不适合其他人直接配使用，如果你对本站的修改模式和成品效果感兴趣的话可以自行按照本站所提供的基础和方法修改出您想要的页面主题。<br>
在这里对原作者表示衷心的敬佩和感谢，如果本文内容有侵权或者其他违规内容，请联系本人，本人会在第一时间进行删除，并作出道歉。
    
## ①对原版主题的修改
    
- 修改原来的标头按钮，增加数量并赋予绝对链接<br>
- 将原本的单页布局改为类似于博客那种层层嵌套<br>
- 取消了对于本来GIthub的链接，增加了页面logo<br>
- 增加了深色模式切换
- ……

## ②修改方法
   
### 修改远程主题配置
[Fork](https://github.com/pages-themes/cayman)主题**Cayman**，在 *_config.yml*中**变更主题名**为你想要的名字，这部分的主题名也是用作你的站店的远程配置名。具体修改格式如下⬇️
  
```yaml
remote_theme: wchenyi/cayman
 ```
### 主题基础配置：
- 在```jekyll-theme-cayman.gemspec*```文件修改改```name```，```title```字段要和*_config.yml*中的字段保持一致
- ```_config.yml```修改```title```和```remote_theme```
  
### 页面元素修改

- **顶部三框修改**
  - 在```layout```文件中选择```default.html```修改```<header class="page-header" role="banner">```字段
- **底部内容修改**
  - 在```layout```文件中选择```default.html```修改```<footer class="site-footer">```字段
  
### 其他修改

- **增加logo显示**
  - 在```layout```文件中选择```default.html```修改```<fhead">```字段，新增以下内容：
```html
<!--网站图标显示方法 ↓ -->
    <link rel="shortcut icon" href="#">
    <link rel="bookmark" href="#">
    <link rel="icon" href="#" />
    <!--Safari图标显示方法 ↓ -->
    <link rel="a#">
    <!--<link rel="apple-touch-icon" sizes="76x76" href="#">
    <link rel="apple-touch-icon" sizes="120x120" href="#">
    <link rel="apple-touch-icon" sizes="152x152" href="#">-->
```
  - 在```_includes```文件选择```head-custom.html```在```<head>```字段增加```<!-- You can set your favicon here -->```下面的内容

- **增加深色模式切换**
  - 在```layout```文件增加了深色模式切换选项（颜色反转，不习惯的不要使用） 

# 3.站点内容

1⃣️本站并不只是一个单纯的下载网站，内部还有很多的说明文档和相关信息推荐。内容会不定时更新，但不能保证最新，也不能保证一定准确和有效；如果对此介意，请慎用。<br>
2⃣️本站说明文档的内容来源于自己的一些思考和油管博主**电丸科技AK**、**不良林**的视频内容，自行进行了整理。如有侵权请联系我进行删除，本人对此给各位大佬造成的不便衷心的感到抱歉！<br>
3⃣️本站最初只是为了自己需要，在网上搜集各种工具的官网地址后以较为舒适的表现形式进行整理。后面内容多了之后整理成一个专门的站点，并为了更好的观感而不断优化界面和内容布局。站点提供包括但不限于以下服务：<br>
- *安卓｜鸿蒙、Windows、Mac、IOS、iPad OS、LInux*等平台的工具下载渠道。
- 对部分软件来源的说明（不含具体使用方法）
- 对科学上网的概念、原理说明
- 转换工具、流媒体拼车平台、谷歌工具
- 个人心得、测评等

# 4.预览效果
在线演示：[点击跳转](https://wangcy.tk/wall) ，如果感兴趣可以Star，想要以此为基础自建的话可以[Fork](https://github.com/login?return_to=%2Fwchenyi%2Fwall)，或者点个[Star](https://github.com/login?return_to=%2Fwchenyi%2Fwall)

| 主页 | 下载页面 | 说明文档 | 原理 |
|--|--|--|--|
| <img src='./shortcuts/主页.png' height='150'/> [跳转](http://wangcy.tk/wall/)  | <img src='./shortcuts/软件下载.png' height='150'/> [跳转](http://wangcy.tk/wall/assets/Android) | <img src='./shortcuts/说明文档.png' height='150'/> [跳转](http://wangcy.tk/wall/assets/doc) | <img src='./shortcuts/原理内容.png' height='150'/> [跳转](http://wangcy.tk/wall/Awall/%E7%BD%91%E7%BB%9C%E7%9A%84%E6%A6%82%E5%BF%B5) |
