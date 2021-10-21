# Java Study







# Java Study 1주차





## 1. Java 컴파일 

> 자바 소스는 JVM 으로 실행되기전에 Java 컴파일(javec) 과정을 거침



- Java 클래스 파일(.java) :  자바의 기본단위 , 클래스 단위

- Java 컴파일러   
  - *.java 파일을 *.class 파일로 변환
  - 실행되는 파일은 아님 , JVM 이 읽기 쉽게 기계어로 변환
- Java 바이트 코드 
  - JVM 이 이해할 수 있는 언어로 변환된 자바 소스 코드
  - 변환되는 코드의 명령어 크기가 1바이트 -> 바이트코드
  - 자바 바이트 코드 확장자는 .class 임



----



## 2. JVM 이란 무엇인가

> Java Virtual Machine , 자바 가상 머신 약자
>
> 자바 바이트코드를 실행하기 위한 가상기계 

- JVM 구성
  - 자바 인터프리터 (interpreter)
  - 클래스 로더 (class loader)
  - JIT 컴파일러 (Just-In-Time-compiler)
  - 가비지 컬렉터 (garbage collector)

- Java Interpreter
  - 자바 소스(.java) >> 자바 컴파일러 >> 자바 바이트코드(.class)  >> 자바 인터프리터로 해석
- Class Loader
  - 자바는 동적으로 클래스를 읽어옴 , 따라서 프로그램이 실행중인 런타임에서야 모든 코드가 JVM 연결
  - 클래스-로더 = 동적으로 클래스를 로딩 
- Just-In-Time-compiler (인터프리터랑은 정적/동적 차이??)
  - 런타임에 실제 기계어로 변환해주는 컴파일러
  - 동적번역 ,  실행속도를 향상시키기 위해 개발
- Garbage Collector 
  - JVM 이 사용하지 않는 메모리 자동 회수



## 3. JRE = Java Runtime Environment

> JVM + Library Classes 
>
> 자바 프로그램을 실행하기 위해 필요함

- JVM 을 실제로 실행되는 도구
- JVM 및 Java Web Start 및 Java Plug-in 포함
- JRE 에서 소스코드 실행 가능? (뭔소리지)
- 패키지 클래스 포함



## 4. JDK = Java Development Kit

> 전체 소프트웨어 개발환경 
>
> JRE , 인터프리터/로더 , 컴파일러(Javac) , 문서 생성기(Javadoc) , 모든 자바 도구 포함

* JVM << JRE << JDK 포함관계





---



# Java Study 2주차



> ## Primitive type
>
> > 8가지의 기본타입이 존재함 , 기본타입은 Null 이 존재하지 않음

| 타입       | 할당되는 메모리 크기 | 디폴트 값 |
| ---------- | -------------------- | --------- |
| boolean    | 1 byte               | false     |
| byte       | 1 byte               | 0         |
| short      | 2 byte               | 0         |
| int (기본) | 4 byte               | 0         |
| long       | 8 byte               | 0L        |
| float      | 4 byte               | false     |
| double     | 8 byte               | false     |



> ## Reference type
>
> > 기본형 타입을 제외한 타입들 , Default 로 Null 을 가지며 NullPointException 발생 가능



> ## Literal
>
> > 소스 코드의 고정된 값을 대표하는 용어



- 값의 형태가 정해져있는 데이터들을 리터럴이라고 표현하는 듯 함
- 일반적으로 쓰는 객체가 아닌 변수 int/float/string 등등 에 해당하는 데이터값을 의미하는듯?



- 정수 리터럴

  - 15

  - 015 (0 : 8진수 표현 = 13)
  - 0x15 (0x : 16진수 표현 = 21)
  - 0b0101 (0b : 2진수 표현 = 5)

- 실수 리터럴 (실수는 기본형이 double 타입임)

  - 0.1234

  - 1234E-4

  - 0.1234f  (뒤에 f 붙이면 float 형)

  - .1234D   (뒤에 D 붙이면 dobule 형 , 안써도 기본 double 형임)

- 문자 리터럴

  - 'S' , "S"

  - char c = \uqe00;  (유니코드 형태로 표현)

  - 특수문자 리터럴
    - `\b` , `\t` , `\n` , `\f`   :  백스페이스 , 탭 , 라인피드 , 폼피드
    - `\r` , `\"` , `\'` ,  `\\`  :  캐리지 리턴 , 이중인용부호 , 단일인용부호 , 백슬래시

- 문자열 리터럴
  - 문자열은 `""`  로만 표현가능하다!!!
  - 문자열은 기본타입이 아님 , Null  값 사용가능

- 논리타입 (boolean)
  - c 와 python 과는 다르게 1/0 으로 사용불가능..



> ## Variable
>



- 변수 명명규칙
  - 변수는 영문자 및 숫자가 사용가능하지만 , 숫자로 시작할 수 없음
  - 특수문자는 `_` 와 `$` 만 사용가능함
  - 변수 이름 사이에는 공백 불가
- 변수 종류
  - 지역변수
    - 내부 함수에서 사용 가능 , 함수 종류되면 사라짐
  - 멤버변수
    - 클래스 내 변수
    - 접근제어가자 public 이면 다른 클래스에서도 사용가능
    - 클래스 인스턴스를 생성하기 전에는 사용불가
  - static 변수
    - 클래스를 메모리에 로드했을때 부터 생성됨
    - 인스턴스를 new 로 생성하지 않아도 사용 가능함
    - 클래스에 딱 1개 존재 , 클래스계의 전역변수 같은 느낌



> ## Array
>

```java

//크기 할당 & 초기화 없이 배열 참조변수만 선언  , 이 상태로는 사용하려 하면 에러남
int[] arr; 
int arr[];

// 배열크기 할당 , 크기를 할당하면 default 값으로 0을 집어넣고 이제 쓸 수 있음
arr = new int[5]; 

// 배열선언 + 초기화 같이하기 , {}로 값을 초기화 선언 할 수 있음 
int[] arr = {1,2,3,4,5}; 
int[] arr = new int[] {1,3,5,2,4}; 
int[] odds = {1,3,5,7,9};
String[] weeks = {"월","화","수","목","금","토","일"};

// 2차원 배열 선언 
int[][] arr = new int[4][3]; 
//3의 크기의 배열을 4개 가질 수 있는 2차원 배열 할당 
int[][] arr9 = { {2, 5, 3}, {4, 4, 1}, {1, 7, 3}, {3, 4, 5}};


```



> ## Type - Inference (타입 추론)
>
> > `var`  :  변수의 타입을 명시적으로 적용하지 않고, 컴파일러가 알아서 초기화 리터럴로 타입 추론 



- 초기화 리터럴로 타입을 추론

- var 는 초기화 값이 있어야 함
- var 는 멤버변수 , 메소드 파라미터 , 리턴 타입으로 사용 불가 (로컬변수로만 가능)

- var 로 선언된 변수는 중간에 타입이 절대로 변경되지 않음 , 특히 자바스킯트

- Lambda Expression 에는 명시적 타입을 지정해줘야 함



---



# Java Study 3주차



## 1. 산술 연산자

> 산술 연산자에는 사칙연산자와 나머지연산자가 있음

```java

/// 1. 사칙연산자 (+,-,*,/)

// int 형에 대한 사칙연산 (double / float / long 에 대해서도 모두 가능하지만 데이터 길이 조심)
int x = 5;  int y = 2;
System.out.printf(" + : %d ,  - : %d ,  * : %d ,  / : %d" ,  x + y , x -y , x*y , x/y);
 
// String 형에 대해서는 + 연산만 작동 , 나머지(-,*,/)는 에러임
String x = "abc";  String y = "123";
System.out.printf(" + : %s"  ,  x + y );    

// char 형에 대해서도 + 연산만 작동하며 , 결과값은 아스키코드값인듯 함
// char 형 은 int형과 + 연산이 가능하지면 연산한값은 char 형으로 받아야 함
char x = 'a';  char y = '1';
System.out.printf(" + : %s"  ,  x + y );


/// 2. 나머지연산자 (%)
// 자바에는 몫을 구하는 연산자가 없다.... 나눈값을 int형변환 시켜서 몫을 구하도록 하자..
// 나머지연산자
int x = 123;  int y = 31;
System.out.printf(" 몫연산 : %d"  ,  x%y );


```



## 2. 비트 연산자

> 비트 연산자는 데이터를 비트 단위로 연산함 

```java

/// 1. 비트 이동 연산자 (<< , >> , >>>)

// "<<" 연산은 이진수로 쪼갠 값들을 2^(자리수 + 비트이동수) 를 SUM 했다고 보면됨 
// ">>" 와 ">>>" 차이는 빈자리를 어떻게 채우냐 차이임
System.out.println("2 << 3 = " + (2<<3)); 
System.out.println("3 << 3 = " + (3<<3)); 
System.out.println("16 >> 3 = " + (16>>3));
System.out.println("-16 >> 3 = " + (-16>>3));
System.out.println("-16 >>> 3 = " + (-16>>>3));

/// 2. 비트 논리 연산자 (& , | , ^ , ~)

// & = AND , | = OR , ^ = XOR , ~ = NOT
// 역시 2진수로 분해해서 비트단위로 연산함 
System.out.println("15 & 25 = " + (15 & 25)); 
System.out.println("15 | 25 = " + (15 | 25)); 
System.out.println("15 ^ 25 = " + (15 ^ 25)); 
System.out.println("~25 = " + (~25)); 

```



## 3. 관계 연산자

> 조건문임 , 생략

## 4. 논리 연산자

> 논리연산자임 , 생략



## 5. instance of

> 해당 Object 가 type 형이 맞는지 확인하는 연산자

`object instanceOf type`

object가 type이거나 type을 상속받는 클래스라면 true를 리턴합니다. 그렇지 않으면 false를 리턴합니다.

```java

// 해당 타입이면 True / 아니면 False 값을 리턴
ArrayList list = new ArrayList();
System.out.println(list instanceof ArrayList);
System.out.println(list instanceof List);

// null 객체에 대해서는 항상 false 값을 리턴함
ArrayList list = null;
System.out.println(list instanceof Object);

```



## 6. assignment(=) 연산자

> 대입연산자 

- 기본 대입연산자 (= , += , -= , *= , /= , %=)  :  사칙연산 + 몫쓰면 됨
- 비트 대입연산자 (|= , ^= , <<= , >>= , >>>=)  :  **어디에 써야할지 잘 모르겠음**



## 7. 3항 연산자

> 3항 연산자 , 간단한 if-else 문을 처리할때 사용하자

`int b = (5 < 4) ? 50 : 40`



## 8. 연산자 우선순위

> 연산자 우선순위는 다음과 같다

- 최우선연산자 ( ., [], () )
- 단항연산자 ( ++,--,!,~,+/-  : 부정, bit변환>부호>증감)
- 산술연산자 ( *,/,%,+,-,shift) < 시프트연산자 ( >>,<<,>>> ) >
- 비교연산자 ( >,<,>=,<=,==,!= )
- 비트연산자 ( &,|,,~ )
- 논리연산자 (&& , || , !)
- 삼항연산자 (조건식) ? :
- 대입연산자 =,*=,/=,%=,+=,-=



## 7. 화살표(->) 연산자 / Java13 - switch 연산자

> 화살표연산자 = 람다식 유사

- Egov 자바는 버전이 낮아서 생략

  





---



