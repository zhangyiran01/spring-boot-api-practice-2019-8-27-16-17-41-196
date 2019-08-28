# spring-boot-api-practice-2019-8-27-16-17-41-196
1.@RestController注解：@Controller和@ResponseBody的合集,表示这是个控制器bean,并且是将函数的返回值直 接填入HTTP响应体中,是REST风格的控制器。
    示例：
   @RestController
    public class HelloController {
    @RequestMapping(value="/hello",method= RequestMethod.GET)
    public String sayHello(){
        return "hello";
    }
}

2.@Service注解：将service层对象注入到spring容器中，和xml配置文件中的<bean></bean>标签作用一样。
  示例：
  @Service("courseDAO")
  @Scope("prototype")
  public class CourseDAOImpl extends HibernateDaoSupport implements CourseDAO{

3.@PathVariable注解：获取参数
   示例：
   public ResponseEntity<Employee> getEmployee( @PathVariable int id) {
        List<Employee> employees = new ArrayList<>();
        Employee employee1 = new Employee(1,"小红",20,"女");
        employees.add(employee1);
       
4.@PostMapping 注解：增加
  示例：
  @PostMapping(path = "/members", consumes = "application/json", produces =  "application/json")
  public void addMember(@RequestBody Member member) {
      //code
      }

5.@PutMapping 注解：用来向服务器提交信息，不过侧重于更新。


6.@Autoweird注解：自动导入依赖的bean
    示例：
   class Demo {
    Class1 clz1;
    Class2 clz2;
    @Autowired
    Class3 clz3;

7.@RequestMapping 注解：用来处理请求地址映射的注解，可用于类或方法上。用于类上，表示类中的所有响应请求的方法都是以该地址作为父路径。
    示例：
      @RequestMapping(value = "/workflow",
      produces = {"application/json"},
      consumes = {"application/json"},
      method = RequestMethod.POST)
      
8.@GetMapping 注解：组合注解，是@RequestMapping(method = RequestMethod.GET)的缩写，该注解将HTTP Get 映射到 特定的处理方法上。
     示例：
   @GetMapping
    public ResponseEntity<List<Employee>> responseEntity() {
        List<Employee> employees = new ArrayList<>();
        Employee employee1 = new Employee(1,"小红",20,"女");
        Employee employee2 = new Employee(2,"小明",18,"男");
        Employee employee3 = new Employee(3,"小王",22,"男");
        employees.add(employee1);
        employees.add(employee2);
        employees.add(employee3);
        return ResponseEntity.ok(employees);
    }
    
9.@RequestParam注解：获取请求参数的值
    示例：
  @RequestMapping
  public Car getCar(@RequestParam("id") long id) {
  }

10.@RequestBody注解：@responseBody注解将controller的方法返回的对象通过适当的转换器转换为指定的格式之后，写入到response对象的body区，通常用来返回JSON数据或者是XML。
     示例：
   @ResponseBody
   @RequestMapping("/hello")
   public String hello() {
    return "Hello World!";
}

11.@DeleteMapping注解：删除URL映射
    示例：
   @DeleteMapping("/pollution/delete/{id}")
   public ResponseData deletePollutionById(@PathVariable("id")String id,    @RequestBody PollutionData data){
    System.out.println(id);
    System.out.println(data);
    return new ResponseData(CodeEnum.SUCCESS.getCode(),MsgEnum.SUCCESS.getMsg(),null);
}
