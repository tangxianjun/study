## Spring

哪些应该放在容器中：dao类，service类，controller类，工具类

哪些对象不应该放在容器中：实体类，数据来自数据库的，Servlet，filter，listener

Ioc概念

idc技术实现di：依赖注入，底层是放射机制

利用容器去创建对象

创建对象的时机：创建spring容器时，创建对象

##### 赋值

set赋值，用xml配置文件设置，只负责调用set方法，不管里面写的什么

构造方法赋值 xml配置文件用constructor-arg标签

#### 注解

component注解，value相当于id，用来创建对象的，在配置文件加入组件扫描器

Repository放在dao的实现类上面的，表示可以访问数据库的

Service用在业务层的，做业务处理的，可以有事务功能

Controller用在控制器上的，接受请求

简单类型的复制@value  无需set方法

引用数据类型 @Autowired @Qualifier按名字注入

@Autowired 的required属性，默认为true，如果对象赋值失败会报错，并且停止执行

@resource注解，jdk提供的，默认先byname，再bytype

IOC主要目的就是解耦合

## AOP面向切面编程

切面： 一般与业务逻辑不相关，事务、日志、统计信息、权限控制等

aop的作用：

- 不修改目标类增强功能
- 减少重复代码
- 专注业务功能实现
- 解耦合 事务功能

通知@Before @AfterRreturning @Around @AfterThrowing @After

切入点表达式execution（访问权限、方法返回值、方法声明（参数）、异常类型）

有接口默认是jdk动态代理，没接口默认是cglib动态代理

## spring 事务处理

spring内部事务管理器管理事务 一个接口和众多实现类

事务隔离级别  mysql默认可重复读 Oracle默认读已提交

- 可重复读 
- 读已提交
- 读未提交
- 串行化

事务的传播级别 总共七个