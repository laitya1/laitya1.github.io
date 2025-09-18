---
layout: post
title: "away靶机渗透"
date:   2025-9-18
comments: true
author: laitya1
---

起手就是信息收集 经典双端口组合

![image-20250918194453556](../assets/image-20250918194453556.png)

如下是以ED25519加密的，还有ECDSA，现在大部分默认是用的rsa算法

![image-20250918203350966](../assets/image-20250918203350966.png)

其实这种还是存在公私钥对的

![image-20250918203404229](../assets/image-20250918203404229.png)

然后开始进行提权，sudo -l发现存在webhook，然后看样子是个成型的工具，可以上github搜索

![image-20250918211043099](../assets/image-20250918211043099.png)

看到启用这个工具要需要一个hooks.json

![image-20250918211609138](../assets/image-20250918211609138.png)

![image-20250918211724421](../assets/image-20250918211724421.png)

然后我在tmp目录下写了一个反弹shell的.sh，id为laitya1，命令工作目录为/tmp，这里要记得给.sh文件加上执行权限

![image-20250918214642094](../assets/image-20250918214642094.png)

  接下来存在能力提权，可以用github对应的提权项目找出来 这里的more存在读和search权限，可以读取shadow文件进行爆破，读取ssh私钥文件进行登录

![image-20250918220232639](../assets/image-20250918220232639.png)

![image-20250918220524939](../assets/image-20250918220524939.png)

这是提取工具项目产生的结果


![image-20250918221321536](../assets/image-20250918221321536.png)



