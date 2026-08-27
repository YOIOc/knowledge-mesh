## Spring MVC的执行流程
##### 视图版本 - JSP
1. 用户发出请求到前端控制器DispatcherServlet
2. DispatcherServlet收到请求调用处理器映射器（HandlerMapping）
3. 处理器映射器找到具体的处理器(接口方法)，生成处理器对象及处理器拦截器(如果有)，再一起返回给DispatcherServlet
4. DispatcherServlet调用处理器适配器（HandlerAdapter）
5. 处理器适配器经过适配(出入参适配)，调用具体的处理器（接口方法执行）
6. 接口方法执行完成返回ModelAndView对象
7. 处理器适配器将接口的执行结构ModelAndView返回给DispatcherServlet
8. DispatcherServlet将ModeAndView传给视图解析器（ViewReslover）
9. 视图解析器解析后返回具体视图（View）
10. DispatcherServlet根据View进行渲染视图（将模型数据填充至试视图）
11. DispatcherServlet响应用户
![700](assets/Spring%20MVC/file-20260827115346356.png)
##### 前后端开发，接口开发
1. 用户请求到前端控制器DispatcherServlet
2. DispatcherServlet收到请求调用处理器映射器
3. 处理器映射器找到具体的接口方法，将接口方法和拦截器(如果有)，一起返回给DispatcherServlet
4. DispatcherServlet调用处理器适配器
5. 处理器适配器对出入参进行适配，调用接口方法
6. 接口方法被@ResponseBody标注，方法将返回结果转换为JSON并响应
![](assets/Spring%20MVC/file-20260827115906222.png)