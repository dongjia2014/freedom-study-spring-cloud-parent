# freedom-study-spring-cloud-eureka-cluster
集群方式部署服务发现组件

## 实现步骤
1. 添加eureka服务器的依赖

```
<dependency>
	<groupId>org.springframework.cloud</groupId>
	<artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
</dependency>
```

2. 给EurekaApplication添加注解@EnableEurekaServer

```
package com.wangguitang.freedom.study.spring.cloud.eureka;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.netflix.eureka.server.EnableEurekaServer;

@SpringBootApplication
@EnableEurekaServer
public class EurekaApplication {

	public static void main(String[] args) {
		SpringApplication.run(EurekaApplication.class, args);
	}
}
```

3. 在配置文件application.yml中添加配置

```
server:
  port: 8761

eureka:
  instance:
    hostname: localhost
  client:
    registerWithEureka: false
    fetchRegistry: false
    serviceUrl:
      defaultZone: http://${eureka.instance.hostname}:${server.port}/eureka/
```

## 启动Eureka服务器
1. 右键类EurekaApplication，选中Run As-->Spring Boot App

