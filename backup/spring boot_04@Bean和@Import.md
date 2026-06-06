# 关于自动扫描
我们知道在spring mvc中要想将每个类添加进spring容器中要在配置文件中<context:component-scan base-package="xxxxx">或者使用@ComponentScan但是在springboot中不需要这个。
这主要是因为为@SpringBootApplication注解也就是主启动类，这个注解主要是有
```java
@SpringBootConfiguration
@EnableAutoConfiguration
@ComponentScan
```
这三个注解中ComponentScan注解如果不添加扫描的范围就会自动扫描打了这个注解的类所属的包及其子包
也就是说如果把主启动类所在位置调到Controller包中其他的包就访问不到了就会出现报错
# 关于@Bean注册

 1. @Component 声明基础注解  @Controller @Component的衍生 标注在控制层上 @Service
  2.  @Component的衍生 标注在业务层上 @Repository @Component的衍生
   3. 标注在数据访问层上(因为数据访问总是和mybatis配合所以用的很少)

# 如何将第三方jar包注入到spring容器中
**使用@Bean注解**
虽然我们无法直接在第三方jar包上写@Component类似的注解，但是我们可以在随意哪个方法中获取到这个类如下，并在哪个方法加上@Bean:
```java
	@Bean
	public User getUser(){
		return new User;
	}
```
而@Bean这个注解，就是将方法返回的对象注入到ioc中这样就可以获取第三方jar包了，当然了这种方式并不规范，正常情况下都是批量处理在配置类中，新建一个config包建一个配置类为其打上@Configuration注解再在配置类下写方法
```java
@Configuration
class configTest{
	@Bean
	public User getUser(){
		return new User;
	}
}
```
**使用@Import**
直接在主启动类上写上@Import(xxx.class)即可导入，经常配合配置类使用
```java
@SpringBootApplication
@Import(ConfigTest.class)
public class DemoApplication {

    public static void main(String[] args) {
        ApplicationContext context= SpringApplication.run(DemoApplication.class, args);
        System.out.println(context.getBean("adda"));
    }

}

```