<!-- logo -->
<p align="center">
    <a href="https://wangcy.tk" alt="Wangcy Logo">
    <img src="https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F9896bb2e-d7f9-41ac-a4e6-5f9ac2d2f652%2FWCY%E7%9A%84%E4%B8%AA%E4%BA%BAlogo.png?table=block&id=e714d3e8-f158-486c-87e0-baa42b87f805" height="173"/></a>
</p>

<!--个人项目跳转页-->
<div align="center">
    <a href="https://wangcy.tk">Home</a> |
    <a href="https://blog.wangcy.cf/">Blog</a> |
    <a href="https://wangcy.tk/wall">Awall</a> <br>
    <a href="https://ycu.wangcy.cf">YCU Start Page </a> |
    <a href="https://sou.wangcy.tk">Minimalist Start Page</a> |
    <a href="https://wangcy.tk/Wallpaper">Wallpaper</a> |
    <a href="https://donate.wangcy.tk">Donate</a> 
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
    <a href="http://wangcy.tk/wall/Eng"><img src="https://img.shields.io/badge/Language-English-brightgreen"></a>
</p>    

# Table of contents
> [1. Website establishment statement](#1-website-establishment-statement)<br>
> [2. Site building process](#2-site-building-process)<br>
> [3. Site content](#3-site-content)<br>
> [4. Preview effect](#4-preview-effect)

# 1. Website establishment statement

> This site is established for the purpose of learning and communication, and the author has nothing to do with the unrelated profit-making and illegal activities. The author of this site neither intends nor advocates the use of the tools and information provided on this site without the permission of the relevant organization or for the purpose of disseminating inappropriate information<br>

> Users please make sure that you have learned the network security knowledge about the causes and working principles of the Great Firewall, criminal law network security crimes, administrative regulations on accessing foreign websites and self-built international Internet channels. If you are not familiar with the above concepts or cannot clearly prohibit the use of the content provided by this site, if you obtain services similar to this site or can achieve the same purpose from other channels, this site has nothing to do with it.<br>

🤣This project is just for fun, if you see it, please raise your hand and correct me for my misconduct. Friends, if you find it useful and fun, you can play it in private, don't take it seriously, and don't spread it.

# 2. Site building process
1⃣️This project was developed by myself with my own knowledge except for the Jekyll template used. Although the implementation principle is very simple, it still has a sense of accomplishment. This film description is also the first time I write README<br>
2⃣️Based on Jekyll's Cayman theme, this site has deeply customized the theme of this site, and the theme of this site is deeply bound to the content of this site. It is not suitable for others to use as their own jekyll theme, please use the original version if you want to use it. Here is the modified part, but please note that I am not a system-trained developer, so the professional vocabulary and content may not be accurate or completely wrong, please bear with me. <br>
3⃣️What is written here is a personalized modification of the original theme [Cayman](https://github.com/pages-themes/cayman), and I deleted the original [README](https://github.com/pages-themes/cayman#readme) for ease of modification. Rewrote the changes you need, if you want to view the original document, please go to the original repository. This topic is only for my project [Wall](https://wangct.tk/wall) to do in-depth customization, so it is not suitable for others to use directly, if you are interested in the modification mode and finished effect of this site, you can modify the page theme you want according to the basis and method provided by this site. <br>
I would like to express my heartfelt admiration and gratitude to the original author, if the content of this article is infringing or other illegal content, please contact me, I will delete it as soon as possible, and apologize.

## ①Modifications to the original theme
        
- Modify the original header button, increase the number and give an absolute link<br>
- Change the original single-page layout to a layer-by-layer nesting similar to a blog<br>
- Canceled the link to the original Github and added the page logo<br>
- Added dark mode toggle<br>
- ...
 
## ②Edit method

### Modify the remote theme configuration
    
[Fork](https://github.com/pages-themes/cayman) theme **Cayman**, **change theme name** in *_config.yml* to the name you want, the theme of this part The name is also used as the remote configuration name for your store. The specific modification format is as follows⬇️
    
```yaml
remote_theme: wchenyi/cayman
 ```
 
 ### Theme basic configuration:
    
- In the ```jekyll-theme-cayman.gemspec*``` file, modify the ```name```, and the ```title``` field should be consistent with the field in *_config.yml*
- ```_config.yml``` modify ```title``` and ```remote_theme```

### Modify page elements
    
- **Modification of the top three boxes**
  - Select ```default.html``` in the ```layout``` file to modify the ```<header class="page-header" role="banner">``` field
- **Bottom content modified**
  - Select ```default.html``` in the ```layout``` file to modify the ```<footer class="site-footer">``` field

### Other modifications
    
- **Increase logo display**
  - In the ```layout``` file, select ```default.html``` to modify the ```<fhead">``` field, and add the following content:
```html
<!--Site icon display method ↓ -->
    <link rel="shortcut icon" href="#">
    <link rel="bookmark" href="#">
    <link rel="icon" href="#" />
    <!--Safari icon display method ↓ -->
    <link rel="a#">
    <!--<link rel="apple-touch-icon" sizes="76x76" href="#">
    <link rel="apple-touch-icon" sizes="120x120" href="#">
    <link rel="apple-touch-icon" sizes="152x152" href="#">-->
```
  - Select ```head-custom.html`` in the ```_includes``` file and add ``` in the field ```<head>```<!-- You can set your favicon here --> ```The following content

- **Added dark mode toggle**

  - Add dark mode switching content in ```layout``` file
    
# 3. Site content
1⃣️ This site is not just a simple download site, there are also a lot of explanatory documents and related information recommendations inside. The content will be updated from time to time, but it cannot be guaranteed to be the latest, nor can it be guaranteed to be accurate and effective; if you mind this, please use it with caution.<br>
2⃣️The content of the explanatory document on this site comes from some of my own thoughts and the video content of YouTube bloggers Dianwan Technology AK and Bad Lin, and I have organized it myself. If there is any infringement, please contact me to delete it. I sincerely apologize for the inconvenience caused to you guys!<br>
3⃣️This site was originally only for your own needs. After collecting the official website addresses of various tools on the Internet, it was sorted out in a more comfortable form. After there is more content later, it will be organized into a dedicated site, and the interface and content layout will be continuously optimized for a better look and feel. The site provides services including but not limited to:<br>

- *Android | Tools download channels for Hongmeng, Windows, Mac, IOS, iPad OS, LInux* and other platforms.
- Description of some software sources (without specific usage methods)
- Explanation of the concept and principle of scientific online
- Conversion tools, streaming ride-sharing platforms, Google tools
- Personal experience, evaluation, etc.

# 4. Preview effect
Online demo: [click to jump](https://wangcy.tk/wall), if you are interested, you can [star](https://github.com/login?return_to=%2Fwchenyi%2Fwall), if you want to build yourself based on this, you can [fork](https://github.com/login?return_to=%2Fwchenyi%2Fwall)

| Home | Download | Instruction | Principle |
|--|--|--|--|
| <img src='./shortcuts/主页.png' height='150'/> [Jump](http://wangcy.tk/wall/)  | <img src='./shortcuts/软件下载.png' height='150'/> [Jump](http://wangcy.tk/wall/assets/Android) | <img src='./shortcuts/说明文档.png' height='150'/> [Jump](http://wangcy.tk/wall/assets/doc) | <img src='./shortcuts/原理内容.png' height='150'/> [Jump](http://wangcy.tk/wall/Awall/%E7%BD%91%E7%BB%9C%E7%9A%84%E6%A6%82%E5%BF%B5) |
