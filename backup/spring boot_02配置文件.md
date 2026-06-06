# 配置文件
**properties配置文件**
使用ide自动创建的spring boot 项目将会自动生成application.properties文件
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/595978d450d4468f95f5295e37f2f323.png)
在项目启动后可以看到tomcat默认的端口和虚拟目录，想要修改就可以在配置文件中修改
```properties
server.port=9090
server.servlet.context-path=/start
```
再次启动后会发现端口和虚拟路径发生了变化
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/1f25304b7b074bd98aadee285186ffcc.png)
**yaml配置文件**
yaml配置文件有两个后缀分别是yml和yaml两者没有本质区别,区别于properties配置文件，yml格式是靠缩进和":"区分
```yml
server:
  port: 9091
  servlet:
    context-path: '/start2'
```
再次启动
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/e092b363cc9748058c148def501b92d8.png)
在实际开发中更加常用yml配置文件，yml文件可读性更强层级更加清晰