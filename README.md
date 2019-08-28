# spring-boot-api-practice-2019-8-27-16-17-41-196
1.@RestControllerע�⣺@Controller��@ResponseBody�ĺϼ�,��ʾ���Ǹ�������bean,�����ǽ������ķ���ֱֵ ������HTTP��Ӧ����,��REST���Ŀ�������
    ʾ����
   @RestController
    public class HelloController {
    @RequestMapping(value="/hello",method= RequestMethod.GET)
    public String sayHello(){
        return "hello";
    }
}

2.@Serviceע�⣺��service�����ע�뵽spring�����У���xml�����ļ��е�<bean></bean>��ǩ����һ����
  ʾ����
  @Service("courseDAO")
  @Scope("prototype")
  public class CourseDAOImpl extends HibernateDaoSupport implements CourseDAO{

3.@PathVariableע�⣺��ȡ����
   ʾ����
   public ResponseEntity<Employee> getEmployee( @PathVariable int id) {
        List<Employee> employees = new ArrayList<>();
        Employee employee1 = new Employee(1,"С��",20,"Ů");
        employees.add(employee1);
       
4.@PostMapping ע�⣺����
  ʾ����
  @PostMapping(path = "/members", consumes = "application/json", produces =  "application/json")
  public void addMember(@RequestBody Member member) {
      //code
      }

5.@PutMapping ע�⣺������������ύ��Ϣ�����������ڸ��¡�


6.@Autoweirdע�⣺�Զ�����������bean
    ʾ����
   class Demo {
    Class1 clz1;
    Class2 clz2;
    @Autowired
    Class3 clz3;

7.@RequestMapping ע�⣺�������������ַӳ���ע�⣬��������򷽷��ϡ��������ϣ���ʾ���е�������Ӧ����ķ��������Ըõ�ַ��Ϊ��·����
    ʾ����
      @RequestMapping(value = "/workflow",
      produces = {"application/json"},
      consumes = {"application/json"},
      method = RequestMethod.POST)
      
8.@GetMapping ע�⣺���ע�⣬��@RequestMapping(method = RequestMethod.GET)����д����ע�⽫HTTP Get ӳ�䵽 �ض��Ĵ������ϡ�
     ʾ����
   @GetMapping
    public ResponseEntity<List<Employee>> responseEntity() {
        List<Employee> employees = new ArrayList<>();
        Employee employee1 = new Employee(1,"С��",20,"Ů");
        Employee employee2 = new Employee(2,"С��",18,"��");
        Employee employee3 = new Employee(3,"С��",22,"��");
        employees.add(employee1);
        employees.add(employee2);
        employees.add(employee3);
        return ResponseEntity.ok(employees);
    }
    
9.@RequestParamע�⣺��ȡ���������ֵ
    ʾ����
  @RequestMapping
  public Car getCar(@RequestParam("id") long id) {
  }

10.@RequestBodyע�⣺@responseBodyע�⽫controller�ķ������صĶ���ͨ���ʵ���ת����ת��Ϊָ���ĸ�ʽ֮��д�뵽response�����body����ͨ����������JSON���ݻ�����XML��
     ʾ����
   @ResponseBody
   @RequestMapping("/hello")
   public String hello() {
    return "Hello World!";
}

11.@DeleteMappingע�⣺ɾ��URLӳ��
    ʾ����
   @DeleteMapping("/pollution/delete/{id}")
   public ResponseData deletePollutionById(@PathVariable("id")String id,    @RequestBody PollutionData data){
    System.out.println(id);
    System.out.println(data);
    return new ResponseData(CodeEnum.SUCCESS.getCode(),MsgEnum.SUCCESS.getMsg(),null);
}
