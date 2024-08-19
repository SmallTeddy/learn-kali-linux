---
description: 该文介绍了刚刚安装的kali系统的一些简易配置
---

# 简易配置

## &#x20;一、root 账号设置

打开 terminal 之后很多操作都会直接在终端进行

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption><p>terminal</p></figcaption></figure>

```sh
sudo passwd root
```

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

这里会先输入 登录用户密码 然后再设置管理员的密码 和 确认密码

{% hint style="info" %}
需要注意的是 这里的密码为密文输入
{% endhint %}

<figure><img src=".gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

修改完成后 我们重新登录

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

此时我们打开 terminal 可以看到红色提示 以及命令行为 # 开头

<figure><img src=".gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

## 二、系统中文修改

后续代码都直接在 root 账号操作 因此不需要带 sudo 命令

```sh
dpkg-reconfigure locales
```

进入语言选择界面，选择 zh\_CN.UTF-8 UTF-8

<figure><img src=".gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

回车确认 重新启动 重启后在弹框中 选择更新名称即可

<figure><img src=".gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

## 三、修改apt安装包的源为国内源

因为Kali自带的源是国外的，经常会因为网络问题，而无法安装或更新软件包。而且国外的源速度很慢。所以我们直接使用国内的源，方便快速。

```sh
vim /etc/apt/sources.list
```

<figure><img src=".gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
vim 编辑器操作：\
按 i 即可切换到输入模式\
按 esc 退出编辑模式\
:wq 保存退出
{% endhint %}

```shell
#中科大Kali源
deb http://mirrors.ustc.edu.cn/kali kali-rolling main non-free contrib
deb-src http://mirrors.ustc.edu.cn/kali kali-rolling main non-free contribshell
```

<figure><img src=".gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

执行命令 检查是否切换成功

```sh
apt update
```

<figure><img src=".gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

## 四、中文输入法安装

```
apt-get install ibus ibus-pinyin
```

<figure><img src=".gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

输入 y 确认安装

<figure><img src=".gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

重新启动 kali 在右上角切换中文输入法

<figure><img src=".gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

## 五、关闭自动锁屏

系统 - 设置 - 电源管理器

<figure><img src=".gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

修改如图配置

<figure><img src=".gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

## 六、生成快照

虚拟机快照管理

<figure><img src=".gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

右键 拍摄快照

<figure><img src=".gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

重命名快照

<figure><img src=".gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

拍摄好之后可以在快照管理里查看

<figure><img src=".gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>
