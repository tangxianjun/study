## MyBatis

不是主动提交事务，update，insert，delete要手动提交事务

Resources类   读取配置文件

#### MyBatis动态代理

mybatis根据dao的接口的方法调用，获取sql语句的信息，mybatis根据dao的接口创建出一个dao接口的实现类，并创建对象完成Sqlsession的调用方法。

sqlsession.getMapper(dao接口)

传参类型parameterType

传递多个参数@Param（"参数名"）

resultType

resultMap修改属性和列的对应

### 动态sql

<if>  <where> <foreach>

#### 数据库配置文件

属性配置文件

mapper多个配合文件，要和接口名一致，并且在同一包下

PageHelper数据分页