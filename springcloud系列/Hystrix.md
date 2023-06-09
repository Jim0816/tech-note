# Hystrix

作用：服务降级、服务熔断、服务限流

**服务降级**
给服务一个兜底保证，返回友好的交互结果，服务降级的发生情况：
1、程序运行异常
2、超时
3、服务熔断触发服务降级
4、线程池/信号量打满

降级解决办法：
1、先解决服务端falback的兜底情况
2、客户端fallback
3、代码优化，兜底代码和业务代码混杂一起，并且代码量膨胀，优化思路：配置全局fallback + 特殊fallback
全局fallback配置：@DefaultProperties

**服务熔断**
达到最大服务访问时，直接拒绝访问，然后调用服务降级方法返回

**服务限流**
高并发场景，让所有服务排队，有序进行