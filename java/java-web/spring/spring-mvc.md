DispatcherServlet

http://cxis.me/2017/04/06/SpringMVC%E6%89%A7%E8%A1%8C%E6%B5%81%E7%A8%8B%E5%8F%8A%E6%BA%90%E7%A0%81%E8%A7%A3%E6%9E%90/

https://hanxlinsist.github.io/Spring-MVC%E6%BA%90%E7%A0%81%E5%89%96%E6%9E%90/


# Spring MVC工作流程
![](/assets/t1p53bo3.45f.jpg)

1. 用户向服务器发送请求，请求被Spring 前端控制Servelt DispatcherServlet捕获；
2. DispatcherServlet对请求URL进行解析，得到请求资源标识符（URI）。然后根据该URI，调用HandlerMapping获得该Handler配置的所有相关
的对象（包括Handler对象以及Handler对象对应的拦截器），最后以HandlerExecutionChain对象的形式返回；
3. DispatcherServlet 根据获得的Handler，选择一个合适的HandlerAdapter。（附注：如果成功获得HandlerAdapter后，此时将开始执行拦截器
的preHandler(...)方法）
4. 提取Request中的模型数据，填充Handler入参，开始执行Handler（Controller)。 在填充Handler的入参过程中，根据你的配置，Spring将帮你
做一些额外的工作：
HttpMessageConveter： 将请求消息（如Json、xml等数据）转换成一个对象，将对象转换为指定的响应信息数据转换：对请求消息进行数据转
换。如String转换成Integer、Double等数据根式化：对请求消息进行数据格式化。 如将字符串转换成格式化数字或格式化日期等数据验证： 验证数
据的有效性（长度、格式等），验证结果存储到BindingResult或Error中.
5. Handler执行完成后，向DispatcherServlet 返回一个ModelAndView对象；
6. 根据返回的ModelAndView，选择一个适合的ViewResolver（必须是已经注册到Spring容器中的ViewResolver)返回给DispatcherServlet ；
7. ViewResolver 结合Model和View，来渲染视图
8. 将渲染结果返回给客户端