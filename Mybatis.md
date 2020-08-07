#Mybatis大致结构
 SqlSession 
 Configuration
 XMLConfigBuilder
##四大神器
 Excutor ：执行器接口，有两个实现类，适配器设计模式
          BaseExcutor:抽象类，实现一部分复杂方法逻辑，一些简单逻辑交给子类处理，有三个子类
	             SimpleExcutor:简单执行器，Mybatis默认，没执行一次update或select 就会创建一个Statement,用完就关闭（可以是Statement或者PreparedStatement对象）
		     ReuseExcutor:可重用执行器，指重复使用Statement,其内部维护一个Map缓存Statement，作用域是同一个Sqlsession
		     BatchExcutor:批处理执行器，将多个sql一次性输出到数据库
	              
	              
	  CachingExcutor:缓存执行器，委托模式，现在缓存查询结果，存在直接返回，不存在委托给相应的Excutor delegate去执行（可以是上面任意一个）。
         
          
 StatementHandler：Statement 处理器，
                 BaseStatementHandler:
		                     SimpleStatementHandler:处理不需要预编译的Sql语句
				     PreparedStatementHandler:处理需要与编译的Sql语句
				     CallableStatementHandler:处理存储过程
		 RoutingStatementHandler:默认处理器，用它判断到底用以上3个中的哪个处理器。

 ParameterHandler
 ResultSetHandler



 
