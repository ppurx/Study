# Content List
  ## OOP
  프로그래밍을 할때 실지에 빗대서 프로그래밍하는 기법을 말한다.
  사물이라고 예를들면 물체는 class 특성은 field 그물체가 할수 있는 행위나 행동등은 method로 정의하여 작성한다.
  소스코드가 직관적이며 유지보수에 용이하다는 장점을 갖고 있다.
  
  ## static
  정적변수로 선언하며 프로세스전체에서 공유하는 변수로 선언된다
  지역변수는 JVM내의 힙영역에 생성되는반면 정적변수는 메소드영역에 생성되어 GC의 영향을 받지않는다.
  
  ## final
  한번 선언하여 다시 변경되지 않을 변수를 선언할때 사용하며 JVM내의 상수풀(permenant area)에 생성되어 변경되지않는다.
  
  ## 제네릭클래스
  클래스를 정의할때 구체적인 클래스를 작성하지않고 선언할때 입력받아 생성되는 클래스로 자료구조에서 많이 사용됨.
  
  ## Interface vs Abstract
  인터페이스 : 추상메소드로만 이루어진(jdk1.8이전)것으로 객체의 행위를 정의하고 하위클래스에서 구현하여 사용한다. 다중상속가능
  추상클래스 : 추상메소드가 하나 이상 있는 클래스로 일반메소드(세부행위)를 정의할 수 있음. 다중상속 불가능
  인터페이스와 추상클래스의 차이점 : 사용할수있는것은 비슷하나, 행위를 정의하고 이를 구현하는목적으로는 인터페이스, 하위클래스들의 공통점이 많아 세부메소드까지 다수 정의해야할경우는 추상클래스가 이득
  
  ## jdk1.8
  람다식, default키워드, G1GC, 
  
  ## Volitile
  변수를 main memory상에 정의해두고 사용한다
  일반 변수는 cpu가 main memory에서 데이터를읽어와 cpu cache 안에 저장해두고 값을사용한다.
  volatile변수는 main memory에 선언해서 읽을때마다 main memory에서 읽어오므로 multi thread환경에서 항상 최신의 값을 보장한다.
  하나의 thread가 write하고 여러 thread가 read할때 가장 효율적
  
  ## thread
  프로세스 안의 여러 작업단위로 작업시 변수불일치와같은 문제를 해결하기위해 synchronized 키워드를 사용하여 상호배제한 변수를 만들어 사용한다.
  
  ## JVM 구조
  - Class Loader : compiler가 java -> class(bytecode) 변환한 class파일을 읽어 RuntimeData Area에 올린다
  - Execution Engine : RuntimeDataArea 에 있는 데이터를 명령어단위로 해석하여 실행함.(초반에 인터프리터기반 지금은 JIT Compiler로 속도보완)
  - RuntimeData Area
    - Method area : 메소드에대한 메타데이터, 정적변수 등 선언 (프로세스단위)
    - Heap area : new 로 생성한 변수들의 정보 (프로세스단위)
    - Stack area : 메소드 콜 정보 (쓰레드단위)
    - PC Register : 쓰레드 사용정보 (쓰레드단위)
    - native Method Stack : java 외 언어 정보 (쓰레드단위)  
    
  ## Heap Memory 구조
  jdk 1.8 이전 은 young영역 / old영역 / permanent 영역 으로 나뉘어있었다
  jdk 1.8 이후 G1GC를 사용하게 될 경우 영역이 바둑판형식으로 변경
  
  ## GC
  java heap memory 내에 사용하는 객체들을 체크하고 사용하지않는객체는 지운다.
  young영역 : minorGC / old영역 : majorGC / 둘다 : full GC
  GC시에는 stop the world 가 발생하여 모든스레드가 정지
  GC 종류 : 
    - Serial
    - pararrel
    - CMS
    - G1GC  
  
  ## immutable
  java에서 한번 할당되면 변경할경우 내용이변경되는게아니라 아예 재할당되는 class를 말한다 (String)
  자주변경되 String은 StringBuilder(단일스레드) 나 StringBuffer(멀티스레드) 를 사용하는것이 바람직하다.
  
  ## 오버라이딩 vs 오버로딩
  오버라이딩 : 상위클래스의 메소드를 재정의하여 사용
  오버로딩 : 같은이름의 메소드의 파라미터만 변경하여 사용
  
  ## 접근제어자
  private(같은클래스내) >  default(패키지내) > protected(패키지내+상속받은외부패키지) > public (전체)
  
  ## Hashcode - Equals 의 상관관계
  equals메소드는 객체가 아예 동일한경우 true를 반환한다.
  객체가 동일한지 여부를 확인할때 hashcode를 사용하여 확인한다.
  hashcode가 동일하다고 무조건 객체가 같은건아니다. 
  
  ## default
  jdk 1.8에서 생긴 interface내의 기능으로 이전의interface는 메소드의 세부내용을 작성할 수 없었지만, default로 작성할수있어짐.
  
  ## Comparator - Comparable
  둘다 정렬할때 사용함
  comparator 는 두변수를 입력받아 어떤게더큰지 확인해서 숫자를반환 -1,0,1
  comparable 인터페이스를 상속받은 클래스는 정렬되어질수있으며 조건으로 동일한 클래스의 객체를 입력받아 this와 비교하여 비교여부를 리턴한다.
  
  ## checkedException vs unCheckedException
  checked Exception : 반드시 예외처리되어야하는 Exception (ex : IOException)
  unchecked Exception : 예외처리하지않아도 컴파일하고 실행되는 Exception (ex : NullPointer Exception, wrongArguments)
  checked exception은 세부적으로 uncecked Exception을 정의하여 출력하는게 디버깅시 편하다.
