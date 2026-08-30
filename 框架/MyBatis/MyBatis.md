## 1.MyBatis的执行流程
1. 读取MyBatis配置文件：mybatis-config.xml加载运行环境和映射文件
2. 通过MyBatis配置文件，构造会话工厂SqlSessionFactory
3. 会话工厂创建SqlSession对象（包含所有执行SQL语句的方法）
4. 
5. 流程结束，关闭SqlSession对象
## 2.MyBatis是否支持延迟加载
MyBatis  