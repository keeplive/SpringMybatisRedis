# SpringMybatisRedis

###项目说明 : 这是一个spring-mybatis-redis整合的项目...使用spring-mvc做控制器..
	
#####主要类在于hxk.dao.redis包的三个类..  

	-RedisCache   :   一个实现了Cache接口的缓存类..  
	
	-SerializeUtil    :   序列化工具类  
	
	-LoggingRedisCache : 自定义缓存的入口，继承MyBatis的loggingCache类  
	
    
 ###   配置 : 添加以下缓存配置 
 
 	`<configuration>
	 <settings>
	        <!-- 这个配置使全局的映射器启用或禁用缓存 -->
	        <setting name="cacheEnabled" value="true" />
	        <!-- 对于未知的SQL查询，允许返回不同的结果集以达到通用的效果 -->
	        <setting name="multipleResultSetsEnabled" value="true" />
	        <!-- 配置默认的执行器。SIMPLE 执行器没有什么特别之处。REUSE 执行器重用预处理语句。BATCH 执行器重用语句和批量更新 -->
	        <setting name="defaultExecutorType" value="REUSE" />
	        <!-- 全局启用或禁用延迟加载。当禁用时，所有关联对象都会即时加载。 -->
	        <setting name="lazyLoadingEnabled" value="false" />
	        <setting name="aggressiveLazyLoading" value="true" />
	        <!-- <setting name="enhancementEnabled" value="true"/> -->
	        <!-- 设置超时时间，它决定驱动等待一个数据库响应的时间。 -->
	        <setting name="defaultStatementTimeout" value="25000" />
	    </settings>
	</configuration>`


###  mapper区别 :

	`<!--  开启二级缓存-->
	<cache eviction="LRU" type="hxk.dao.redis.LoggingRedisCache"/>
	
	以及在select语句中使用useCache="true" 属性`	


