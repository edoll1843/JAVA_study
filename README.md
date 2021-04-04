# Java의 기본 구조

```java
public class Main {   <--- Main은 xxx.java의 파일 명과 같아야한다. Main이름의 클래스 선언, public이라서 다른 클래스에서 접근 가능
  public static void main(String[] args) { <--- 자바는 main()에서 실행 시작 public static void로 선언
  
    System.out.println("Hello World!");
    
  }
}
```
# java의 데이터 타입

문자열은 기본타입이 아니다.

String 클래스로 문자열 표현한다

```java
String Name = "LJH";
Name +1.8   --> "LJH1.8"
"(" + 3 + "," + 5 ")" --> "(3,5)"
System.out.println(Name + "이정호"); --> "LJH이정호" 
```
# 논리 타입
```java
c++에선 bool로 선언했지만 java는 boolean으로 선언
boolean a = true;
boolean b = 10 > 0;   --> 참임으로 true;
boolean c = 1;    <-- 안된다. 타입이 일치 하지 않는다. C++과 달리 java는 1,0을 참,거짓으로 사용 못함
```
# 상수 선언
```java
C++ -> const
java -> final

final int a = 1;
//static으로 선언하는 것이 바람직
static final int a = 1;
```

# var키워드
```java
java 10 부터 도임
C++의 auto같은거
타입 생략하고 변수 선언이 가능
컴파일러가 추론하여 변수 타입 결정
//////변수 선언 시 초깃값이 주어지지 않으면 컴파일 오류///////
////var는 지역변수 선언만 가능////
```
# 자바의 입력과 출력
```java
System.out.println()    ---> 개행기능이 있음
System.out.print()      ---> 개행 없음
Scanner 클래스 --> 읽은 바이트를 문자,정수,실수,불린,문자열 등 다양한 타입으로 변환하여 리턴 
```
```java

//키보드에 연결된 System.in에게 키를 읽게 하고 원하는 타입으로 변환하여 리턴
//Scanner는 입력되는 키 값을 공백으로 구분되는 토큰 단위로 읽음

import java.util.Scanner; // 헤더 필요

public class javacodingtest{
        public static void main(String[] args)
    {
        System.out.println("이름,도시,나이,체중,독신여부");

        Scanner scan = new Scanner(System.in); // Scanner 객체 생성
        String name = scan.next(); // 다음
        String city = scan.next(); // string 다음
        int age = scan.nextInt(); // int 형
        int weight = scan.nextInt();
        boolean single = scan.nextBoolean();
        System.out.println(name + city + age + weight + single);
        scan.close();
    }
    
}
```
# 자바의 배열

1. int arr [];
2. int arr = new int [5];

* 배열 선언
int arr[]; 또는
int[] arr;

이렇게 하면 안됨 int arr[5]; <--- 기존의 C++처럼 하면 안됨

* 배열 생성
int arr[];
arr = new int[5];       <--- 선언 먼저 하고 공간 할당

int arr[] = new int[5];  <--- 선언과 동시에 배열 생성

* 배열 초기화
int arr[] = {1,2,3,4,5};

C++은 함수에서 배열과 크기를 각각 받지만
java는 arr.length로 크기를 알 수 있다.

* 2차원 배열 선언

int arr[][];

* 2차원 배열 생성

int arr[] = new int[2][5];  <--- 선언과 동시에 생성

* 배열 리턴

배열의 래퍼런스만 리턴(배열 전체가 리턴되는 것이 아님)

```java
int[] returnarr()
{
  int temp[] = new int[4];
  return temp;
}
```

```java

public class ReturnArray {
static int[] makeArray() {
int temp[] = new int[4]; 
for(int i=0; i<temp.length; i++)
temp[i] = i; // 배열 초기화, 0, 1, 2, 3
return temp; // 배열 리턴
}
public static void main(String[] args) {
int intArray[]; 
intArray = makeArray(); // 메소드가 리턴한 배열 참조
for(int i=0; i<intArray.length; i++) <--- makeArray가 종료돼도 생성된 배열은 소멸되지 않아서 가능
System.out.print(intArray[i] + " ");
}
}
```

# 자바의 예외처리

try-catch-finally문
//finally는 생략 가능

try
{
  예외가 발생할 가능성이 있는 실행문
}
catch(처리할 예외 타입 선언)
{
  예외 처리문
}
finally
{
  예외 발생 여부와 상관없이 무조건 실행되는 문장
}

자바는 응용플로그램이 실행 중 오류를 탐지 할 수 있도록 많은 예외 클래스 형태로 제공

예외 타입(예외 클래스)             예외 발생 경우

ArithmeticException               정수를 0으로 나눌때 발생 java.lang

NullPointerException            null을 참조할 때 발생  java.lang

ClassCastException              변환 할 수 없는 타입으로 객체를 변환할떄발생  java.lang

OutOfMemoryError                메모리가 부족한 경우 발생  java.lang

ArrayIndexOutOfBoundsException  배열의 범위를 벗어난 접근 시 발생  java.lang

IllegalArgumentException        잘못된 인자 전달시 발생  java.lang

IOException                     입출력 동작 실패 또는 인터럽트 시 발생  java.io

NumberformatException           문자열이 나타내는 숫자와 일치하지 않는 타입의 숫자로 변환시 발생  java.lang

InputMismatchException      Scanner의 nextInt()를 호출하여 정수로받으려고했는데 사용자가'a'입력하면 발생  java.util


# 자바 객체 지향 특성 : 상속

상위 클래스의 맴버를 하위 클래스가 물려받는다.

상위 클래수 : 수퍼클래스
하위 클래스 : 서브클래스, 수퍼클래스 코드의 재사용, 새로운 특성 추가 기능

class Animal{
//상위, 수퍼클래스
  String name;
  int age;
} 

class Human extends Animal    <--- extends로 상속받는다. Human클래스는 Anumal의 객체도 사용 가능
{
  String hobby;
  String job;
}

# 자바 객체 지향 특성 : 다형성

다형성 : 같은 이름의 메소드가 클래스 혹은 객체에 따라 다르게 구현되는것.

* 메소드 오버로딩 : 한 클래스 내에서 같은 이름이지만 다르게 작동하는 여러 메소드
* 메소드 오버라이딩 : 슈퍼 클래스의 메소드를 동일한 이름으로 서브 클래스마다 다르게 구현

# 기본 생성자

어떤 클래스를 선언하고 메인에서
 func pizza = new func(); 가 있을 때
 
 클래스 안에서 따로 생성자를 지정하지 않으면 기본생성자 호출하지만
 
 public class func{
  ...
  ...
  ...
  
  public func(int a)
      변수 = a;
 }
 따로 생성자를 선언하면 컴파일러는 기본 생성자를 자동 생성해 주지 않는다.
 만약 생성함수에 인자가 없다면 오류가 난다.

# this
  객체 자신에 대한 레퍼러스
```java

public class food{
  int name;
  public food(int name)
  {
    this.name = name;   <--- 첫번째는 클래스 맴버, 두번째는 레퍼런스
  }
}
```

# 자바의 접근 지정자

4가지
private, protected, public, 디폴트(접근지정자 생략)


접근 지정자의 목적
* 클래스나 일부 멤버를 공개하여 다른 클래스에서 접근하도록 허용
* 객체 지향 언어의 캡슐화 정책은 멤버를 보호하는 것(접근 지정은 캡슐화에 묶인 보호를 일부 해제할 목적)

접근 지정자에 따른 클래스나 멤버의 공개 범위

private -> 디폴트 -> protected -> public

외부로부터 완벽차단 -> 동일 패키지에 허용 -> 동일패키지/자식클래스에 허용 -> 모든 클래스에 허용


# static 멤버

non-static 멤버는 객체가 생성될 떄, 객체마다 생긴다.
but, static 멤버는 클래스당 하나만 생성한다. 객체들에 의해 공유된다.

```java
class simple
{
  int n;
  static int m;
}
```

static 멤버 m은 b1객체가 생성되기 전에 존재한다.

simple b1 = new simple();     ---> b1 n  하나의 m
simple b2 = new simple();     ---> b2 n  하나의 m(b1의 m과 공유함)
simple b3 = new simple();     ---> b3 n  하나의 m(b1,b2의 m과 공유함)

static 메소드는 non-static 사용 불가
non-static 메소드는 static 멤버 사용 가능

static 메소드는 this 사용 불가

# final 클래스와 메소드

final 클래스 - 더 이상 클래스 상속 불가능

final 메소드 - 더 이상 오버라이딩 불가능

# 자바 상속의 특징

 클래스 다중 상속 물허
 * C++은 다중 상속 가능 그래서 멤버가 중복 생성되는 문제가 있음
 
 모든 자바 클래스는 묵시적으로 Object클래스를 상속받음
 * java.lang.Object 클래스는 모든 클래스의 슈퍼 클래스

# 업캐스팅

업캐스팅
* 서브 클래스의 레퍼런스를 슈퍼 클래스 레퍼런스에 대입
* 슈퍼클래스 레퍼런스로 서브 클래스 객체를 가리키게 되는 현상

```java
class person{}
class student extends person{}

person p;
student s = new student();
p = s;// 업캐스팅
```

# 다운캐스팅

다운캐스팅
* 슈퍼클래스 레퍼런스를 서브 클래스 레퍼런스에 대입
* 업캐스팅된 것을 다시 원래대로 되돌리는 것
* 반드시 명시적 타입 변환 지정

```java
class person{}
class student extends person{}

person p = new Student("이정호"); // 업캐스팅

student s = (student)p; // 다운캐스팅, 강제 타입 변환

```

# 래퍼클래스(Wrapper Class)

자바의 자료형은 기본타입, 참조타입으로 나뉜다.
기본 타입 : char, int, double 등등
참조 타입 : class, interface 등등
기본 타입의 데이터를 객체로 표현해야 하는 경우가 있다.
기본 자료타입을 객체로 다루기 위해서 사용하는 클래스들을 Wrapper class라고한다.
자바는 모든 기본타입은 값을 갖는 객체를 생성 할 수 있다.
이런 객체를 포장 객체라고도 한다. 그 이유는 기본 타입의 값을 내부에 두고 포장하기 때문
래퍼클래스로 감싸고 있는 기본 타입 값은 외부에서 변경 할 수 없다. 하고싶다면 새로운 포장객체를 만들어야한다.
```java
기본타입  래퍼클래스(Wrapper class)
byte  ---> Byte
char  ---> Character
int   ---> Integer
float ---> Float
double---> Double
boolean---> Boolean
long  ---> Long
short ---> Short
```
기본 타입의 값을 포장 하는 걸 박싱(boxing) 반대로 포장객체에서 기본타입의 값을 얻어내는걸 unboxing이라고함
```java
Integer num = 18; // 자동 박싱
int n = num;      // 자동 언박싱
```
