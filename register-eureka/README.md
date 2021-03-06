注册中心 Eureka Server
=======================

启动：

```Bash
mvn spring-boot:run
```

启动后，可以通过

```
http://localhost:8000/
```
进入管理界面，查看当前连接上来的微服务

## 创建Eureka Server
pom中增加依赖

```xml
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
</dependency>
```
启动类添加注解
```java
@EnableEurekaServer
@EnableDiscoveryClient
```

## 其它项目在Eureka中登记

下面的操作**不是**在这个项目（register-eureka)中做，而是在需要在eureka server中登记的微服务项目内做。
    
[sample-service](../sample-service)已经实现下面的这些步骤，启动后会自动登记在此项目创建的eureka server。

pom中增加依赖

```xml
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
</dependency>
```
启动类添加注解

```java
@EnableEurekaClient
```
application.yml添加配置

```yml
eureka:
  client:
    serviceUrl:
      defaultZone: http://localhost:8000/eureka #Eureka Server地址，可以写多个（逗号隔开）用于集群
  instance:
    preferIpAddress: true
```
