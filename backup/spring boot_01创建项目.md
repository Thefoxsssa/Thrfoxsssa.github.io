最近做项目深深感到基础不足故滚回来复习spring boot 和vue
# 创建工程
****
**导入jar包**
在maven中的pom文件导入此坐标，或者在ide中选择创建spring boot工程选择spring boot 版本和spring web选项选择create即可。
```xml
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-web</artifactId>
</dependency>
```
**创建controller**
创建一个controller包在里面创建一个普通java类“HelloController”打上@RestController注解方法上打上@RequestMapping注解并写上地址代码如下:
```java
	package com.wwcc.controller;

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;
//此注解表示这是一个控制层类，并会在spring启动后自动生成beans
//rest表示不使用分发器拼接前后而是直接返回hello spring
@RestController
public class HelloController {
    @RequestMapping("/hello")
    public String helloSpring(){
        return "hello spring";
    }
}
```
**创建spring主启动类**
创建App类之后，给他打上@@SpringBootApplication,在其主函数中写上ApplicationContext applicationContext= SpringApplication.run(App.class,args);spring主启动类就创建好了。
```java
package com.wwcc;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.ApplicationContext;

/**
 * Hello world!
 *
 */
@SpringBootApplication
public class App 
{
    public static void main( String[] args )
    {
        ApplicationContext applicationContext= SpringApplication.run(App.class,args);

    }
}

```
**关于pom文件**
如果你是使用ide直接创建spring工程而不是maven项目那么ide帮你创建的工程中pom文件会有如下字样:
```xm
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>3.5.14</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>
```
**测试**
前置条件完成后启动spring主启动类，由于spring boot内嵌了tomcat默认端口为8080所以在项目启动后tomcat也会自动启动，包括项目里的@RestController类，所以直接在浏览器访问127.0.0.1:8080/hello即可看见如下图

<img width="495" height="160" alt="Image" src="https://github.com/user-attachments/assets/fbe3be7f-524f-4b98-8355-a920c9e1d58d" />