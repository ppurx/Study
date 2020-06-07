# [Spring](https://github.com/ppurx/PrepareInterview/blob/master/Spring)
  
  ## 의존성
  A class의 a method가 B class를 생성하고 b method를 사용할경우 A->B 는 의존한다 라고 표현한다.
  의존성이 높아질 경우 Bclass가 변경됨에따라 Aclass도 변경해야할 가능성이 높아져 유지보수성이 좋지않은 소프트웨어가 작성된다.
  
  ## DI
  직접적으로 A->B로 의존성을 생성하지않고 외부객체에서 A.a(B) 로 생성하거나,  A.a.set(B.b()) 로 setter를 활용하여 전달하는 방식으로
  의존성을 주입하여 B가 변경되더라도 A가 변경되지 않도록 한다.
  
  ## IoC
  개발자가 작성한코드가 다른코드를 직접 부를때 그 제어는 개발자에게 있다 라고 표현한다면 이 제어권을 FrameWork에 양도하여 Framework가 개발자의 코드를 실행하도록 함으로써 개발자는 직접 bean생성같은 작업을 코드로 작성하지 않아도 된다.
  
  ## AoP
  OOP를 보완하기 위해 나온 개념으로 비즈니스로직 외에 운영상,관리상의 필요한 기능들을 모아 공통기능으로 분류하여 만들고 이를 특정부분에 적용하는 프로그래밍 기법
    - Aspect : 구현할 공통기능
    - Advice : Aspect가 적용되는 시점 (Around , After , Before ...)
    - JoinPoint : Aspect를 적용할 수 있는 여러 메소드들
    - PointCut : JoinPoint 중 실제 Aspect를 적용(Weaving)한 메소드
        
  ## Spring 구조
  사용자 -> Filter -> Dispatcher Servlet -> Handler Mapper(Request Mapping) -> Dispatcher Servlet -> Controller -> service -> Dispatcher Servlet -> View Resolver -> Filter -> 사용자
  
  ## Filter vs Interceptor
  Filter는 Dispatcher servlet 호출전후, Interceptor 는 dispatcher Servlet에서 controller를 호출하기 전후로 적용
  endpoint 관리를위해서는 filter가 편하고, bean을 비교적 자유롭게 사용가능한건 interceptor
  
  ## 어노테이션
  문법적 의미는 주석 이라는 의미로 메소드나 클래스등에 @기호를 사용하여 적용하며 여러 기능을 담당하게끔 임명할 수 있음
  - Component : component-scan을 선언에 의해 특정 패키지 안의 클래스들을 스캔해서 Bean 을 생성
    Controller
    service
    repository
  - RequestMapping : url의경로와 controller를 매핑한다.
  - RestController : controller + responseBody , view가 필요없이 내용만전달할때 사용하며 spring 4.0에서 생김
  - responseBody : response를 json객체로 전달
  - Required : setter메소드에 사용하며 데이터를 반드시채워야할때 사용, xml로 데이터를 입력해주는형식으로 체크
  - Autowired : type에 따라서 알아서 bean을 주입해준다. (type 매칭안되면 이름으로찾음)
  - Qualifier : autowired 사용시 name로 강제확인해서 bean 주입
  
  ## Parameter 전달방법
  - @RequestParam : parameter값을 받아온다
  - @PathValue : 구분자를 사용한 uri로 전달받을때 사용 (Rest API에서 많이사용) @postmapping과 사용 /indx/{idx}
  - @RequestBody : POST데이터 처리
  - @ModdelAttribute : form값으로 받은데이터 처리
    
  ## bean을 주입받는방법
  - 생성자 : AllArgsConstructor (권장)
  - setter : 
  - Autowired
    
  ## jpa vs SQL Mapper
