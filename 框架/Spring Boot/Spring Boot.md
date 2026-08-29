## 1.Spring Boot相较于Spring框架，开发更高效的原因
- 原因一：**起步依赖**—解决“依赖引入繁琐”的问题
	- 痛点：在传统Spring项目中，开发Web项目需要引入很多依赖（Spring Core、Spring MVC、Jackson、Tomcat等）。还需要花大量时间排查是否存在版本不兼容的问题
	- 优势：开发Web项目，仅需要引入`spring-boot-starter-web`依赖，Maven会自动通过依赖传递，把所有Web的相关jar包一同拉取下来，同时保证版本互相兼容
- 原因二：**自动配置**—解决“大量xml配置”的问题
	- 痛点：在传统Spring项目中，即使引入依赖，还需要配置大量的xml配置文件
	- 优势：Spring Boot启动时，自动将一些配置类、Bean对象加入到IOC容器中，无需手动声明与配置（Spring Boot默认约定大于配置）
## 2.Spring Boot自动配置原理
1. **@SpringBootApplication**：封装了三个子注解
	- @SpringBootConfiguration：该注解用来声明当前类是一个配置类
	- @EnableAutoConfiguration：SpringBoot实现自动配置的核心注解
	- @ComponentScan：组件扫描注解，默认扫描当前引导类所在包及其子包
2. **@EnableAutoConfiguration**：封装了@Import注解
3. **@Import(AutoConfigurationPackage.class)**
	Spring Boot会将@Import注解导入的类，实例化为Bean加入到IOC容器中
4. **AutoConfigurationPackage.class**
	该类实现了SelectImport接口的`String[] selectImports()`方法
5. **String\[] selectImports()**
	该方法会将 该项目+所有外部Jar包 的`classpath:META-INF/spring/xxx.import`文件中配置的配置类，统一以一个字符串数组的形式返回
6. 
## 1.Spring Boot中配置的优先级（由高到低）
1. 命令行参数（--xxx=xxx）
2. Java系统属性（-Dxxx=xxx）
3. application.properties
4. application.yml
5. application.ymal