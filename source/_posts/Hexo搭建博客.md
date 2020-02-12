---
title: Hexo+Github搭建博客
date: 2020-01-03 13:20:55
tags: [Hexo, linux,  github]
categories: 杂项
---
# Hexo+Github搭建博客

使用Hexo+Github快速搭建个人博客
<!-- more -->


## 1、准备工作
- 安装node.js
```bash
sudo apt-get install nodejs
```
- 安装npm
```bash
sudo apt-get install npm
```

+ 查看版本信息`npm -v` &&`nodejs -v`;
+ 升级npm`sudo npm -g npm`;
+ 再次确认版本信息`npm -v` &&`nodejs -v`，此时你可能会遇到显示升级了，但是查询版本信息的时候还是原来的版本的情况，不要慌，重新注销登入下就行了。

- 可选步骤    
由于npm源在国内访问比较比较忙，这样下载的时候就会很忙甚至出错，所以最好将npm的源换成国内的
    - 方式一：安装cnpm    
         cnpm是阿里定制的npm 命令行工具，安装命令
        ```bash
        sudo npm install -g cnpm --registry=https://registry.npm.taobao.org
        ```
    - 方式二：设置npm镜像源    
    如果你不想使用cnpm则使用
        ```bash
        npm config set registry https://registry.npm.taobao.org
        ```
        再输入:把npm源换成国内的。
        ```bash 
        npm config list
        ```
    
    - 设置系统代理
* github账号    
创建一个`username.github.io`的项目，注意username一定要是你github账户的名称，否则不行，这点很重要。

## 安装Hexo博客框架
```bash
sudo cnpm install -g hexo
```
### 初始化Hexo
使用命令`Hexo init` 注意必须是空文件夹(不能有文件或者隐藏文件),期间会有警告,不用理会
### 测试
使用命令`hexo s`启动Hexo    
访问<http://localhost:4000/>
可以看见里面有一篇文章,并且有相关的教程


## 安装部署到github插件
安装Github快速部署插件可以很方便的将你的Hexo博客部署到你的Github上面。
```bash
npm install hexo-deployer-git --save
```
## 修改个人信息
注意有多个_config.yml文件，Hexo有_config.yml，有一些主题还有_config.yml文件实在不同的文件夹下面的，首先修改Hexo目录下的_config.yml，把它里面的信息全部改成你自己的信息

    title: 标题
    subtitle: 副标题
    description: 描写
    keywords: '关键字'
    author:  作者
    language: zh-CN语言
    timezone: 时区(可不设置)
    
    
    # Deployment
    ## Docs: https://hexo.io/docs/deployment.html
    deploy:
    type: git
    repo:改成你的git项目链接
    branch:master  ,也可以不指定

## 进行测试
shell中分别执行这些命令
```bash
 hexo c
 hexo g
 hexo s
 ```
 此时如果正确无误的话可以再访问<http://localhost:4000/>查看修改过后的信息有没有错误。


 ## 更换主题
 >[主题推荐1](https://www.zhihu.com/question/24422335/answers/updated)
 >[安装教程](https://github.com/yscoder/hexo-theme-indigo/wiki)

 >[主题推荐2](https://blog.csdn.net/zgd826237710/article/details/99671027)   

 >[Hexo主题排行榜](https://www.hexothe.me/)    
 
 我这里用的是indigo这个主题,主题更换起来十分的方便,你可以在Hexo文件夹下的/Theme文件夹下使用多个主题,这样一旦你觉得那个主题看腻了,就能够很方便的更换（_在_config.yml配置文件下修改主题_）。更换主题后有一些主题设置需要修改，查看主题的配置文档就行了，很详细。
 ## 写文章
 Hexo的文章全部采用MarkDown格式,如何使用markdown写博客参考[MarkDown语法教程](https://www.mdeditor.com/)，比较简单，不懂的话就在这个网站看一看，相当于是一本字典，不懂就翻一翻。写好的文章放在`source/_posts`文件夹下面就可以了

 ## 最后确认
 当你觉得差不多的时候后，进行确认，shell中分别执行这些命令访问<http://localhost:4000/>查看
```bash
 hexo c
 hexo g
 hexo s
 ```
 ## 部署大功告成
 执行 
 ```bash
 hexo c
 hexo g 
 hexo d
 ```
 按照要求输入github账号密码就能够部署成功了！！