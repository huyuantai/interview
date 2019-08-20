https://mp.weixin.qq.com/s/3TSkT9AYZduJ2CEfAIx7vg?tdsourcetag=s_pcqq_aiomsg
spring boot 项目

# spring boot 启动原理
- 1.起步依赖分析
- 2.自动配置原理


#### 自动配置原理
Spring Boot 的开启注解是：@SpringBootApplication，由下面组成
- @Configuration
- @ComponentScan
- @EnableAutoConfiguration

http://tengj.top/2017/03/09/springboot3/
https://my.oschina.net/u/3039671/blog/787195

###　@EnableAutoConfiguration
１.加载不同classpath所有的META-INF/spring.factories这个文件，从这个文件中提出key为org.springframework.boot.autoconfigure.EnableAutoConfiguration的值，而这些值就是一些自动配置类

如：mybatis提供的META-INF/spring.factories内容
> Auto Configure
org.springframework.boot.autoconfigure.EnableAutoConfiguration=\
org.mybatis.spring.boot.autoconfigure.MybatisAutoConfiguration
