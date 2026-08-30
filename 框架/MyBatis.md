## 1.MyBatis的执行流程
1. 通过mybatis-config.xml，创建SqlSessionFactory对象实例
2. 调用SqlSessionFactory.openSession()方法，获取一个SqlSession
3. 调用SqlSession.getMapper()方法，获取Mapper接口的实现类（动态代理）
4. 执行Mapper的数据库操作方法