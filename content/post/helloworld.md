---
title: "关于后端技术的选型"
date: 2022-11-06T22:37:17+08:00
hero: /img/1.png
authors: 
    - Ezio Sweet J. Ding
---
## 异步技术

我们更新仓库时肯定不能一个一个更新，而是同时启动多个更新任务，这要求使用异步技术，在Go语言，只推荐使用语言原生支持的**goroutine**协程技术

## 同步技术

在同步的技术上基本上没的选，Go语言能用的rsync wrapper十分有限，只有以下几个
+ **grsync** [https://github.com/zloylos/grsync](https://github.com/zloylos/grsync)
+ **go-sync** [https://github.com/Redundancy/go-sync](https://github.com/Redundancy/go-sync)
+ **gSync** [https://github.com/c4milo/gsync](https://github.com/c4milo/gsync)

**建议使用grsync**

## web服务器

go语言的web server很多，但是没有一个能像Java里的Spring那样自成一套体系的，所以以下均只提供最基础的web服务

+ **iris** [https://www.iris-go.com/docs/#/](https://www.iris-go.com/docs/#/)
+ **beego** [https://github.com/beego/beego](https://github.com/beego/beego)
+ **fiber** [https://docs.gofiber.io/](https://docs.gofiber.io/)
+ **gin** [https://gin-gonic.com/zh-cn/docs/](https://gin-gonic.com/zh-cn/docs/)
+ **echo** [https://echo.labstack.com/](https://echo.labstack.com/)

**建议 iris>beego>gin=echo=fiber**

iris的生态比较好且性能极为出众，beego占有国人开发的优势，gin和echo的生态很好但性能不如iris，fiber的性能极为出众但是生态不如iris

## 数据库选型

建议使用关系型数据库

个人建议：
**TiDB>Oceanbase>Mariadb=pgsql>其他**

TiDB是国产的分布式关系型数据库，其语法和接口协议遵循MySQL 5.7规范，性能和体积都很好

### 管理数据库

+ Navicat
+ Goland可用自带的Database管理
+ VSCode可用[Database Client](https://marketplace.visualstudio.com/items?itemName=cweijan.vscode-database-client2)插件

## ORM框架

ORM框架即对象映射框架，用来链接应用和数据库的

+ xorm [https://xorm.io/zh/](https://xorm.io/zh/)
+ gorm [https://gorm.io/zh_CN/](https://gorm.io/zh_CN/)

两个差不多，看着办吧，我倾向于xorm

## 日志框架

打印日志

+ zap [https://pkg.go.dev/go.uber.org/zap](https://pkg.go.dev/go.uber.org/zap)
+ logrus [https://github.com/Sirupsen/logrus](https://github.com/Sirupsen/logrus)

我平常写东西也不打印日志的，两个都是蛮好的
## 定时任务(Cron)

+ gocron [https://github.com/go-co-op/gocron](https://github.com/go-co-op/gocron)
+ cron [https://github.com/robfig/cron](https://github.com/robfig/cron)

**强烈建议gocron，这个是cron的二次封装，易用性很高**
## IoC框架(可选)

控制反转是Java中Spring框架发扬光大的一种思想，旨在将控制权从人的手中交给IoC容器，我们获取实例不再采用new的方式，而是从容器中拿取现成的，这是Java的一个思想，可能并不适用于Go

+ Alibaba/IOC-golang [https://ioc-golang.github.io/](https://ioc-golang.github.io/)
+ iocgo [https://github.com/studyzy/iocgo](https://github.com/studyzy/iocgo)

