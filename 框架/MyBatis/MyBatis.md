## 1.MyBatis的执行流程
1. 读取MyBatis配置文件（mybatis-config.xml），构造会话工厂SqlSessionFactory
2. 调用SqlSessionFactory.openSession()方法，创建会话对象SqlSession
3. 调用SqlSession.getMapper()方法，生成Mapper接口的动态代理对象
4. 调用Mapper对象中的SQL操作方法
5. 流程结束，关闭SqlSession对象
## 2.MyBatis是否支持延迟加载
MyBatis  