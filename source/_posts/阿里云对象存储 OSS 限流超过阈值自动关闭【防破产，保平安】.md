---
title: 阿里云对象存储 OSS 限流超过阈值自动关闭【防破产，保平安】
date: 2023-03-26 11:56:44
tags: 
- 阿里云oss
categories: 教程
---



## 场景



使用对象存储，遇到恶意盗刷流量，不能及时发现，搞不好会“破产”的。市面上的云服务器对象存储，都没有带宽限制（单链接限速不算），也没有超过流量阈值，自动停止的功能。甚至有些拒绝恶意IP访问都不可以。。。这种状况已经持续很多年了

（设置referer 设置防盗链是挡不住恶意刷流量的 https://help.aliyun.com/document_detail/31869.html ）



**“对象存储破产案例“:D**

https://www.v2ex.com/t/269463?p=1

https://developer.aliyun.com/ask/196191

https://segmentfault.com/q/1010000000718083

https://segmentfault.com/q/1010000007911554



## **原因**

阿里云给的解释是“考虑到一键关闭会导致客户的业务受到影响，因此OSS暂时没有提供此功能”。

网上有人说，貌似是因为对象存储的结构不能及时统计用户的流量使用。对一些超级流量大户，短时间也会有巨额流量费用。。。阿里云，七牛云都没有这个。





## 解决方法

我发现一种方法好像可以解决。是个好思路，过阵子，些代码测试一下。原理是，对象存储报警有个回调功能，可以使用回调功能请求 OSS 的接口，修改 OSS Bucket 的读写权限为私有，这样直接禁止所有人消耗 OSS 流量。



**第一步，对象存储报警**

![img](https://raw.githubusercontent.com/xiangchengkang/blogImage/main/img/1587147934833.jpg)



![img](https://raw.githubusercontent.com/xiangchengkang/blogImage/main/img/1587147859457.jpg)





**第二步，回调设置对象存储读写权限**



对象存储 OSS API 中有个接口 PutBucketACL，可以设置 Bucket 的读写权限。PutBucketACL 接口用于修改存储空间（Bucket）的访问权限。

```sql
PUT /?acl HTTP/1.1
x-oss-acl: Permission
Host: BucketName.oss-cn-hangzhou.aliyuncs.com
Date: GMT Date
Authorization: SignatureValue
```



PutBucketACL接口通过Put请求中的x-oss-acl请求头来设置权限，如果没有该请求头，权限设置不生效。

取值：public-read-write、public-read、private。



https://help.aliyun.com/document_detail/31960.html





