SpringBoot之class is not visible from class loader
    方案一，排查掉spring-boot-devtools模块模块的maven引入可以解决，这时候所有类都是使用APPClassloader加载。
    方案二，可以引入spring-boot-devtools模块，但是禁用禁用reStart功能 
    public static void main( String[] args )
   {
       System.setProperty("spring.devtools.restart.enabled", "false");
 
       SpringApplication.run(Application.class, args);
   }
   
   dubbo默认超时会重试两次，这样的重试有时会产生很大问题，所以建议关闭。关闭有两种方式：

在服务上加注解:
@Service(interfaceClass = AccountUpdateApi.class,retries = -1)
注意这里重试次数写成-1，经测试，dubbo版本(2.6.0)写成0无效。
另一种方式，配置文件：spring.dubbo.provider.retries=-1
   
阿波罗在本机存放配置的位置：对于Windows，文件位置为C:\opt\settings\server.properties

localhost:1.1.10 bufanxiang$ java -cp druid-1.1.10.jar com.alibaba.druid.filter.config.ConfigTools ghtyIJK55%
privateKey:MIIBVgIBADANBgkqhkiG9w0BAQEFAASCAUAwggE8AgEAAkEAhEvi9ouXMosU21JQYIJMkcSvQtKd78ymTjR2oxix2h+WaRy7fCIxAf16G5iLNZfbSqsE4dO+frjzByAIVOT9zwIDAQABAkBIvXjjWkkd7z7egFnVVo9HLr+2nBteuEVQhqQcdP2FEkJX3H2tWtUWYzKeMfEaogysW7Qty7t1C8U4R7KnQ4pRAiEAxAf8yrPyEVni8G4p15j451+63x6Fn/Qt3tHhRW8yDrUCIQCsxJD17ToJy3tHRRQ5lR/qtSBs2mUkkwuuUPlmyfno8wIhALUr0KUiY5FHqqacmc0pErj7z4CP+91V1eL9xB3g47mVAiEAnbGxivekUQptFMllw4VtI4N9/D1/slmRgOOiMYNL26cCIQC88wjk47LqNZZSsXXmSqAgNBIH64d7Pd6uMCB/96k9Cg==
publicKey:MFwwDQYJKoZIhvcNAQEBBQADSwAwSAJBAIRL4vaLlzKLFNtSUGCCTJHEr0LSne/Mpk40dqMYsdoflmkcu3wiMQH9ehuYizWX20qrBOHTvn648wcgCFTk/c8CAwEAAQ==
password:K6jdol+65WZ14LJ+33mlmPxoMJAgkNGOhxUnuv6PSbRA/gP+77X1h938ijB1w3/4Ixd3H76OHhQ/hdG9p0Qq3g==