---
layout:     post
title:      "See you, Again "
subtitle:   "GitHub。"
date:       2020-07-09
author:     "Hok"
header-img: "img/post-bg-seeyou.jpg"
tags:
  - Github
  - Git
    
---


###### 本地blog部署到github



###  git ssh key配置

要使本地与git连接，就需要配置ssh key

```
# ssh-keygen -t rsa -C "这里换上你的邮箱"
ssh-keygen -t rsa -C "zhixue@hok.ink"
```

确认秘钥的保存路径（如果不需要改路径则直接回车）；
如果上一步选择的保存路径下已经有秘钥文件，则需要确认是否覆盖（如果之前的秘钥不再需要则直接回车覆盖，如需要则手动拷贝到其他目录后再覆盖）；
创建密码（如果不需要密码则直接回车）；
确认密码；
创建成功后，在指定的路径下会生成2个名为id_rsa和id_rsa.pub的文件：

id_rsa 为私钥

id_rsa.pub 为公钥



### 远程仓库设置

#### 1. 注册登录github

#### 2. 创建repository  

​	例如 改名为 hok-ink.github.io

   #huh

#### 3. 设置添加ssh key

​	点击GitHub.com 网页右上角头像

​	选择【settings】

​	跳转后 点击左边【SSH and GPG keys】

​	点击 【new key】 增加ssh key(公钥) ，创建名称， 复制 id_rsa.pub 文件里的公钥 ‘ssh AAAA.........@zhixue.hok.ink' 到内容框 。



### 本地仓库设置

#### 1. 创建本地git仓库

```
mkdir hok-ink.github.io
cd hok-ink.github.io
然后初始化仓库
git init
查看仓库状态
git status
复制相关博客模板/网站文件到仓库后
git add .
编辑提交记录
git commit -m 'update blog'  # 提交已经ADD进来的改动，并添加说明
连接远程仓库
git remote add origin 'github.com/hok-ink/hok-ink.github.io' 
提交已确认的修改到远程仓库
git push -u origin master
```

#一些git 命令 （忽略）

```
查看和修改用户名和邮箱
$ git config --list //查看全局配置
$ git config user.name
$ git config user.email //查看
$ git config --global user.name "username"
$ git config --global user.email "email" //修改

获取远程Git repo,创建local copy.
$ git clone [url] //创建的repo将会以url最后一个/后面的名称命名创建文件夹
$ git clone [url] newname //指定特定的名称

提交代码
$ git add . //递归地添加当前工作目录中的所有文件
$ git commit -m "the commit message" //提交已经ADD进来的改动，并添加说明

免用户名和密码push
当使用https拉取项目后，每次进行push、pull等操作时会需要我们填写用户名和密码。无疑这样很繁琐，所以可以设置一下实现免用户名和密码push：
检查是否有credential.helper设置，没有的话为空：
$ git config -l|grep credential.helper
$ git config credential.helper manager
```



#### 2. 域名设置 

购买域名   例： xxx.com

渠道：万网/阿里云/掘金等

 添加域名解析

| 主机记录 | 记录类型 | 解析线路 | 记录值            |
| -------- | -------- | -------- | ----------------- |
| blog     | CNAME    | 默认     | hok-ink.github.io |
|          |          |          |                   |

然后回到远程仓库[hok-ink.github.io] 

创建**CNAME**文件   并在文件中编辑 blog.hok.ink   然后commit

/>>Settings>>GitHub pages 设置中>>将Custom domain 设为  blog.hok.ink

保存



然后就可以通过  blog.hok.ink 访问你的博客了![post-seeyou-1](\img\in-post\post-seeyou-1.jpg)



以后再去折腾 博客网站自动部署到远程服务器里

