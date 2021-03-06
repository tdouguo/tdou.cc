---
title: Nginx 常用命令
iscopyright: true
comments: true
lang: cn
tags:
  - nginx
  - command
categories:
  - 服务器
abbrlink: nginx
date: 2019-08-11 16:52:01
---


- Nginx 综合命令
    ```
        $ /etc/init.d/nginx start
        $ /etc/init.d/nginx stop
        $ /etc/init.d/nginx restart
        $ nginx　　启动nginx
        $ nginx -v　　查看版本
        $ nginx -t　　测试配置文件是否有语法上的错误等
    ```

- 重新加载配置文件
    ```
        $ /etc/init.d/nginx -s reload 
        $ ngxin -s reload
    ``` 

- 停止nginx
    ```
        $ /etc/init.d/nginx -s stop
        $ ngxin -s stop
    ``` 

- 查看nginx 进程运行情况
    ```
        $ ps -ef |grep nginx
    ``` 

- Nginx 服务
    ```
        $ service nginx start
        $ service nginx stop
        $ service nginx restart
    ``` 
