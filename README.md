# spring-boot-api-practice-2019-8-27-16-17-41-196

```
1.@Controller
      标识一个Spring类是Spring MVC controller处理器，用于处理http请求。
      
2.@ResponseBody 
      用于将Controller的方法返回的对象，根据HTTP Request Header的Accept的内容,通过适当的HttpMessageConverter转换为指定格式后，写入到Response对象的body数据区。
      使用时机：返回的数据不是html标签的页面，而是其他某种格式的数据时（如json、xml等）使用；
      
3.@RestController
      是@Controller和@ResponseBody的结合体，两个标注合并起来的作用。
      
4.@Service
　　　用法：用于标注业务层组件(Service层)上 
　　　作用：标注于业务层组件上表示定义一个bean，自动根据所标注的组件名称实例化一个首字母为小写的bean。 
　　　实例解释：IocCarService类被标注为一个bean,bean名称为iocCarService,此时该类已经被spring纳入管理中，待使用。
  
5.@PathVariable 
      用于接收路径参数，比如@RequestMapping(“/hello/{name}”)申明的路径，将注解放在参数中前，即可获取该值，通常作为Restful的接口实现方法。
      
6.@RequestMaping
   当前台界面调用Controller处理数据时候告诉控制器怎么操作。
   用法：1.标记于一个被@Controller标注的类上 
　　　　2.标记于被@Controller标注类里面的方法上面 
　　　作用：用法1，表示该被标注类下面所有方法的父类标注（可以理解为所有用法2“继承”用法1）@RequestMaping有六个属性value、method、consumes、produces、params、headers 
　　　value：指定浏览器请求的地址； 
　　　method：指定请求的method类型， GET、POST、PUT、DELETE等； 
　　　consumes：指定处理请求的提交内容类型（Content-Type），例如application/json, text/html； 
　　　produces：指定返回的内容类型，仅当request请求头中的(Accept)类型中包含该指定类型才返回； 
　　　params：指定request中必须包含某些参数值是，才让该方法处理； 
　　　headers：指定request中必须包含某些指定的header值，才能让该方法处理请求； 
　　　实例解释：如果要在浏览器访问Action类中的carRun方法，只需要本地域名+端口号+该标注所定义的value值即可(127.0.0.1:8080/car/carRun)　　 
　　　@RequestMaping常用的记住value和method，更详细的介绍——》链接
   
7.@GetMapping
@RequestMapping(method = RequestMethod.GET)的简写
作用：对应查询，表明是一个查询URL映射

8.@PostMapping
@RequestMapping(method = RequestMethod.POST)的简写
作用：对应增加，表明是一个增加URL映射

9.@PutMapping
@RequestMapping(method = RequestMethod.PUT)的简写
作用：对应更新，表明是一个更新URL映射

10.@DeleteMapping
@RequestMapping(method = RequestMethod.DELETE)的简写
作用：对应删除，表明是一个删除URL映射

11.@Autowired
这个注解的作用是将其他的类，接口引入，类似于之前的类的初始化等，用这个注解，类中或接口的方法就可以直接调用了。

12.@RequestParam
用于获取提交的参数。用法如下：
@RequestMapping("/")
public String Demo1(@RequestParam String lid){
    System.out.println("----"+lid);
    return null;
}

13.@ResponseBody
将HttpRequest的请求体映射为Java的POJO对象。一般Get方法是没有body的，在post数据的时候可以指定json数据。对于想要转换的格式，记得要添加对应的依赖包。比如json的，添加Gson。或者jackson，必要时还要配置一下converter的bean。
