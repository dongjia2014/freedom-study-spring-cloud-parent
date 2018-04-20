# freedom-study-spring-cloud-client
此项目为微服务框架的eureka-client


## 实现步骤
1. 添加eureka-client的依赖

```
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
		</dependency>
```

2. 给EurekaClientApplication添加注解@EnableEurekaClient

```
package com.wangguitang.freedom.study.spring.cloud.eureka.client;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.netflix.eureka.EnableEurekaClient;

@SpringBootApplication
@EnableEurekaClient
public class EurekaClientApplication {

	public static void main(String[] args) {
		SpringApplication.run(EurekaClientApplication.class, args);
	}
}

```

3. 在配置文件application.yml中添加配置

```
server:
  port: 8080
  
spring:
  application:
    name: eureka-client
eureka:
  client:
    serviceUrl:
      defaultZone: http://localhost:8761/eureka
```

## 启动Eureka-client
1. 右键类EurekaClientApplication，选中Run As-->Spring Boot App