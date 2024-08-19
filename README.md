---
description: 本文详细介绍了如何在 Mac 电脑的 VMWare 上安装 Kali Linux 系统
---

# 系统安装

## 一、Kali Linux 系统介绍

Kali Linux是一个基于Debian的Linux发行版，旨在进行高级渗透测试和安全审计。Kali Linux包含数百种工具，适用于各种信息安全任务，如渗透测试，安全研究，计算机取证和逆向工程。Kali Linux由公司Offensive Security开发，资助和维护。

Kali Linux于2013年3月13日发布，Kali的前身是基于BackTrack Linux，自上而下的重建，完全符合Debian开发标准。

Kali的优势和特性：

1. 包括900多种渗透测试工具
2. 免费：完全免费且永远都是。你将永远不必支付Kali Linux的费用
3. 开源：所有进入Kali Linux的源代码都可供任何人使用
4. 广泛的无线设备支持：我们已经构建了Kali Linux以支持尽可能多的无线设备，允许它在各种硬件上正常运行，并使其与众多USB和其他无线设备兼容
5. 在安全的环境中开发： Kali Linux团队由一小部分人组成，他们是唯一可信任的提交包并与存储库交互的人，所有这些都是使用多个安全协议完成的
6. GPG签名包和存储库： Kali Linux中的每个包都由构建和提交它的每个开发人员签名，并且存储库随后也会对包签名
7. ARMEL和ARMHF支持： Kali Linux可用于各种ARM设备

## 二、官网下载镜像

官网地址：

{% embed url="https://www.kali.org/" %}

<figure><img src=".gitbook/assets/image (29).png" alt=""><figcaption><p>官网</p></figcaption></figure>

点击 Download，选择对应的系统

<figure><img src=".gitbook/assets/image (30).png" alt=""><figcaption><p>下载镜像</p></figcaption></figure>

我这里下载第一个 Installer Images

## 三、在 VMWare 中安装

点击新增虚拟机

<figure><img src=".gitbook/assets/image (31).png" alt=""><figcaption><p>创建虚拟机</p></figcaption></figure>

点击 **从光盘或映像中安装**



<figure><img src=".gitbook/assets/image (32).png" alt=""><figcaption><p>创建虚拟机</p></figcaption></figure>

选择下载好的镜像

<figure><img src=".gitbook/assets/image (33).png" alt=""><figcaption><p>镜像选择</p></figcaption></figure>

点击继续，选择 Debian 12.x 64 位 Arm

<figure><img src=".gitbook/assets/image (34).png" alt=""><figcaption><p>系统选择</p></figcaption></figure>

点击继续

<figure><img src=".gitbook/assets/image (35).png" alt=""><figcaption><p>虚拟机配置</p></figcaption></figure>

在自定设置中 更改虚拟机名称

<figure><img src=".gitbook/assets/image (36).png" alt=""><figcaption><p>重命名</p></figcaption></figure>

点击完成，开机

<figure><img src=".gitbook/assets/image (39).png" alt=""><figcaption><p>开机</p></figcaption></figure>

选择图形化安装 Graphical install

<figure><img src=".gitbook/assets/image (38).png" alt=""><figcaption><p>图形化安装</p></figcaption></figure>

选择简体中文，方便学习

<figure><img src=".gitbook/assets/image (40).png" alt=""><figcaption><p>语言选择</p></figcaption></figure>

地区选择中国

<figure><img src=".gitbook/assets/image (41).png" alt=""><figcaption><p>国家选择</p></figcaption></figure>

语言选择汉语

<figure><img src=".gitbook/assets/image (42).png" alt=""><figcaption><p>语言选择</p></figcaption></figure>

等待安装组件

<figure><img src=".gitbook/assets/image (43).png" alt=""><figcaption><p>组件安装</p></figcaption></figure>

配置主机名，可以跟我一样

<figure><img src=".gitbook/assets/image (44).png" alt=""><figcaption><p>主机设置</p></figcaption></figure>

注册一个用户名

<figure><img src=".gitbook/assets/image (45).png" alt=""><figcaption><p>账号设置</p></figcaption></figure>

设置密码 这里随意就可以

<figure><img src=".gitbook/assets/image (46).png" alt=""><figcaption><p>密码设置</p></figcaption></figure>

磁盘分区可以不做修改 使用第一个选项

<figure><img src=".gitbook/assets/image (47).png" alt=""><figcaption><p>磁盘选择</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (48).png" alt=""><figcaption><p>磁盘选择</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (49).png" alt=""><figcaption><p>磁盘选择</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (50).png" alt=""><figcaption><p>磁盘选择</p></figcaption></figure>

这里要注意修改为 是

<figure><img src=".gitbook/assets/image (51).png" alt=""><figcaption><p>磁盘选择</p></figcaption></figure>

点击后等待系统安装

<figure><img src=".gitbook/assets/image (52).png" alt=""><figcaption><p>安装系统</p></figcaption></figure>

选择要默认安装的软件 这里按照默认勾选即可 如没有勾选 top10 等 请注意勾选

<figure><img src=".gitbook/assets/image (53).png" alt=""><figcaption><p>选择软件</p></figcaption></figure>

点击继续后 等待软件安装 该时间些许漫长 请耐心等待

<figure><img src=".gitbook/assets/image (54).png" alt=""><figcaption><p>软件安装</p></figcaption></figure>

安装结束后 自动重启

<figure><img src=".gitbook/assets/image (55).png" alt=""><figcaption><p>结束安装进程</p></figcaption></figure>

输入账号密码登录系统

<figure><img src=".gitbook/assets/image (27).png" alt=""><figcaption><p>登录</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>
