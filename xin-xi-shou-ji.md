---
description: 本文详细介绍了在渗透过程中，如何去进行信息收集。
---

# 三、信息收集

## 一、被动信息收集概述

### 1、被动信息收集概述和目的

信息收集的方式可以分为两种：被动和主动。

被动信息收集方式是指利用第三方的服务对目标进行访问了解，比例：Google搜索。

主动的信息收集方式：通过直接访问、扫描网站，这种将流量流经网站的行为。比如：nmap扫描端口。

被动信息收集的目的：通过公开渠道，去获得目标主机的信息，从而不与目标系统直接交互，避免留下痕迹

### 2、信息收集内容

1. IP地址段
2. 域名信息
3. 邮件地址
4. 文档图片数据
5. 公司地址
6. 公司组织架构
7. 联系电话 / 传真号码
8. 人员姓名 / 职务
9. 目标系统使⽤的技术架构
10. 公开的商业信息

### 3、信息用途

1. 信息描述目标
2. 发现目标
3. 社会工程学攻击
4. 物理缺口

## 二、DNS域名解析原理-收集网站域名解析记录

### 1、DNS服务概述

#### （1）DNS 服务器概述：

DNS（Domain Name Server，域名服务器）是进行域名(domain name)和与之相对应的IP地址 (IP address)转换的服务器。DNS服务器分为根域DNS服务器、顶级域名DNS服务器。根域DNS服务器有13个，都存储了全部的顶级域名服务器的所在地址

#### （2）DNS查询过程

1. 浏览器缓存：当用户通过浏览器访问某域名时，浏览器首先会在自己的缓存中查找是否有该域名对应的IP地址（若曾经访问过该域名且没有清空缓存便存在）；
2. 系统缓存:当浏览器缓存中无域名对应IP则会自动检查用户计算机系统Hosts文件DNS缓存是否有该域名对应IP；
3. 路由器缓存：当浏览器及系统缓存中均无域名对应IP则进入路由器缓存中检查，以上三步均为客户端的DNS缓存；
4. ISP（互联网服务提供商）DNS缓存(一般就是本地DNS服务器):当在用户客户端查找不到域名对应IP地址，则将进入ISP DNS缓存中进行查询。比如你用的是电信的网络，则会进入电信的DNS缓存服务器中进行查找；
5. 根域名服务器：当以上均未完成，则进入根服务器进行查询。全球仅有13台根域名服务器，1个主根域名服务器，其余12为辅根域名服务器。根域名收到请求后会查看区域文件记录，若无则将其管辖范围内顶级域名（如.com）服务器IP告诉本地DNS服务器；
6. 顶级域名服务器：顶级域名服务器收到请求后查看区域文件记录，若无则将其管辖范围内主域名服务器的IP地址告诉本地DNS服务器；
7. 主域名服务器：主域名服务器接收到请求后查询自己的缓存，如果没有则进入下一级域名服务器进行查找，并重复该步骤直至找到正确记录；
8. 保存结果至缓存：本地域名服务器把返回的结果保存到缓存，以备下一次使用，同时将该结果反馈给客户端，客户端通过这个IP地址与web服务器建立链接。

（3）DNS查询方式： 递归查询和迭代查询

1. 主机向本地域名服务器的查询一般都是采用递归查询。
2. 本地域名服务器向根域名服务器的查询是迭代查询。

<figure><img src=".gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

递归：客户端只发一次请求，要求对方给出最终结果。

迭代：客户端发出一次请求，对方如果没有授权回答，它就会返回一个能解答这个查询的其它名称服务器列表，客户端会再向返回的列表中发出请求，直到找到最终负责所查域名的名称服务器，从它得到最终结果。

### 2、DNS信息收集

#### （1）将域名解析为IP地址

```bash
ping www.baidu.com
```

<figure><img src=".gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>

#### （2）使用nslookup查看域名

```bash
nslookup www.baidu.com
```

<figure><img src=".gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>

#### （3）DNS信息收集-DIG

> 语法： dig  (选项)  需要查询的域名
>
> @\<DNS服务器地址>： 指定进行域名解析的域名服务器；
>
> any  #显示所有类型的域名记录。默认只显示A记录

```bash
dig www.baidu.com
```

<figure><img src=".gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
可以使用 - x 参数反查域名
{% endhint %}

```bash
dig -x 114.114.114.114
```

<figure><img src=".gitbook/assets/image (61).png" alt=""><figcaption></figcaption></figure>

#### （4）查询网站的域名注册信息和备案信息

#### 1、域名注册信息的两种查询方式，Web接口查询和Whois命令查询

通过Web接口查询：

* 阿里云：[https://whois.aliyun.com/](https://whois.aliyun.com/)
* 站长之家：[http://whois.chinaz.com/](http://whois.chinaz.com/)

<figure><img src=".gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure>

Whois命令查询

```bash
whois www.baidu.com
```

<figure><img src=".gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

#### 2、备案信息查询

Web接口查询：

[http://icp.chinaz.com/](http://icp.chinaz.com/)  或  [https://icp.aizhan.com/](https://icp.aizhan.com/)&#x20;

<figure><img src=".gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>

天眼查

[https://www.tianyancha.com/](https://www.tianyancha.com/)&#x20;在这里可以进一步查看企业的一些信息。

通过 [https://beian.miit.gov.cn/](https://beian.miit.gov.cn/) 查找域名12306.cn的备案信息

<figure><img src=".gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>

### 3、收集子域名信息

#### （1）子域名介绍

顶级域名是域名的最后一个部分，即是域名最后一点之后的字母，例如在http://example.com这个域名中，顶级域是.com（或.COM），大小写视为相同。

常见的顶级域主要分2类：

1. 通用顶级类别域名常见的有：用于工商金融企业的.com；用于教育机构的.edu；用于政府部门的.gov；用于互联网络信息中心和运行中心的.net；用于非盈利组织的.org。
2. 国家及地区顶级域，如".cn"代表中国，".uk"代表英国等，地理顶级域名一般由各个国家或地区负责管理。.jp代表什么？

子域名（Subdomain Name），凡顶级域名前加前缀的都是该顶级域名的子域名，而子域名根据技术的多少分为二级子域名，三级子域名以及多级子域名。

#### （2）挖掘子域名的重要性

子域名是某个主域的二级域名或者多级域名，在防御措施严密情况下无法直接拿下主域，那么就可以采用迂回战术拿下子域名，然后无限靠近主域。

例如：www.xxxxx.com 主域不存在漏洞，并且防护措施严密。而二级域名  edu.xxxxx.com存在漏洞，并且防护措施松散。

（3）如何挖掘子域名

1. 搜索引擎挖掘 如： 在Google中输入 site:qq.com
2. 第三方网站查询：[http://tool.chinaz.com/subdomain、https://dnsdumpster.com/](http://tool.chinaz.com/subdomain%E3%80%81https:/dnsdumpster.com/)
3. 证书透明度公开日志枚举：[https://crt.sh/](https://crt.sh/)
4. 子域名挖掘工具 ：Layer子域名挖掘机

## 三、使用Layer子域名挖掘机收集子域名信息

### 1、Layer子域名挖掘机工具介绍

Layer子域名挖掘机是一款域名查询工具，可提供网站子域名查询服务。拥有简洁的界面、简单的操作模式，支持服务接口、暴力搜索、同服挖掘三种模式，支持打开网站、复制域名、复制IP、复制CDN、导出域名、导出IP、导出域名+IP、导出域名+IP+WEB服务器以及导出存活网站。

安装可在该 [地址](https://github.com/SmallTeddy/learn-kali-linux/releases/tag/%E6%B8%97%E9%80%8F%E5%B7%A5%E5%85%B7%E5%8C%85%E5%90%88%E8%AE%A1) 下载，启动Layer，在win10下运行Layer

{% hint style="info" %}
Layer需要 .NET环境支持
{% endhint %}

<figure><img src=".gitbook/assets/image (71).png" alt=""><figcaption></figcaption></figure>

在域名右侧的文本框输入想要搜索的域名，比如ke.qq.com

如果要使用自定义字典，请把字典文件命名为dic.txt，放到跟程序同目录下，程序会自动加载字典。

如果没有自定义字典，程序会自动使用内置字典，内置字典总共175万多条数据，内容包括了常用子域名，以及3000+常用单词和1-3位所有字母。

如果要爆破二级以下域名，可以直接填入要爆破的子域名，程序会自动拼接下一级子域。比如填入ke.qq.com，程序会爆破 .ke.qq.com下面的域名。

<figure><img src=".gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (73).png" alt=""><figcaption></figcaption></figure>

## 四、使用资产检索FOFA搜索引擎收集信息

## 五、ARL资产侦察灯塔系统搭建及使用

## 六、Google搜索引擎使用技巧

## 七、利用漏洞库查询漏洞信息
