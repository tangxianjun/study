## Maven

#### 核心概念

- POM ：poom.xml ，项目对象模型，maven的核心
- 约定的目录结构
- 坐标 ：是一个唯一的字符串
- 依赖管理 ： 管理项目的jar文件
- 仓库管理 ：资源的存放位置
- 生命周期 ：构建项目的过程
- 插件和目标 ：执行maven构建时用到的工具是插件

#### 配置maven

1. 去官网下载
2. 配置环境变量 M2_HOME  path添加bin

#### maven约定的目录结构

每个maven项目是一个文件夹

```
---/src
-------/main    #放主程序java代码
-----------/java #程序的包和包中的java代码
-----------/resources   #java程序使用的配置文件
-------/test    #放测试文件代码，可以没有
---/pom.xml    maven核心文件，每个项目有一份
```

编译

`mvn compile`	

配置本地仓库地址

修改maven的settings.xml文件

#### 仓库

maven使用的插件和项目使用的jar包

#### pom.xml

- modeVersion
- groupId    一般域名到写
- artifactId  项目名称
- version    版本号
- packaging   打包后压缩文件名默认 jar
- dependencies和dependency 项目中要使用的资源
- properties 属性
- build 项目构建时的配置信息

mvn package 打包主程序

#### 依赖范围

scope ： compile test provided

#### maven属性设置

