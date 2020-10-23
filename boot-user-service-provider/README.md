# 说明
springboot 整合dubbo

1. 新建springboot项目
2. pom.xml添加dubbo依赖，springboot2以后依赖dubbo0.2.0版本
```xml
    <dependency>
      <groupId>com.alibaba.boot</groupId>
      <artifactId>dubbo-spring-boot-starter</artifactId>
      <version>0.2.0</version>
    </dependency>
```
3. 启动类注解 @EnableDubbo 开启dubbo
4. 服务提供者：service类注解 com.alibaba.dubbo.config.annotation.Service 暴露服务
5. 服务提供者：application.properties文件 添加一下配置
```
   dubbo.application.name=user-service-provider # 应用名
   dubbo.registry.address=127.0.0.1:2181  # zookeeper注册地址
   dubbo.registry.protocol=zookeeper   # 注册中心地址协议
   
   dubbo.protocol.name=dubbo   # 服务提供者协议配置
   dubbo.protocol.port=20880   # dubbo协议缺省端口为20880
   
   dubbo.monitor.protocol=registry #监控中心配置
```
6. 消费者：引用时@Autowired换成@Reference（com.alibaba.dubbo.config.annotation.Reference）
```java
    @Reference
    UserService userService;
```
7. 消费者：application.properties文件，配置如下
```
    server.port=8081   #monitor中心占用了8080
    dubbo.application.name=boot-order-service-consumer #应用名
    dubbo.registry.address=zookeeper://127.0.0.1:2181 #相当于下边两行
    # dubbo.registry.address=127.0.0.1:2181  # zookeeper注册地址
    # dubbo.registry.protocol=zookeeper   # 注册中心地址协议
    dubbo.monitor.protocol=registry #监控中心
```
          	



