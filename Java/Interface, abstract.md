## Interface
> 
- 메소드의 몸체를 갖지 않는다
- 인스턴스 생성 불가, 참조변수 선언 가능 
- 상속은 다중상속이 되지 않지만 구현(implements)은 여러개 가능

```java
interface Printable{
  public void print(String doc); // 메소드의 몸체 X
}   

class Printer implements Printable {
  public void print(String doc) {
    System.out.println(doc);
  }
}

  // 인터페이스형 참조변수 선언 가능
  Printable prn = new Printer();
  prn.print("Hello); 
```
```java
class Robot extends Machine implements Movable, Runnable(){...}

Robot r = new Robot // 모든 것 사용 가능
Machine ma = new Robot // Machine에서 override된 것만 사용 가능
Movable mo = new Robot // Movable에서 override된 것만 사용 가능
```

- 인터페이스에 선언되는 메소드와 변수
```java
interface Pirntable {
  public static final int PAPER_WIDTH = 70; // 멤버변수는 무조건 publics static final로(생략 가능)
  public satiic final int PAPER_HEIGHT = 120; 
  public void print(String doc); // 메소드는 무조건 public (생략 가능)
```

- 인터페이스의 상속
```java
interface Printable {
  void print(String doc);
}

interface ColorPrintable extends Printable{ // 인터페이스의 상속
  void printCMYK(String doc);
}

class Sprinter implements Printable{
 ...    // 흑백의 경우에 기존 클래스 수정할 필요 없어짐
} 

class prn909Drv implements ColorPrintable{ // Color프린트인 경우
  @Override
  public void print(String doc) { // 흑백 출력
    System.out.println("black & whtie ver"); 
    System.out.print(doc);
  }
  @Override
  public void printCMYK(String doc){
  System.out.println("CMYK ver");
    System.out.print(doc);
  }
}

- 디폴트 메소드 
  - 인터페이스 간에 상속하지 않고도 인테페이스 수를 늘리지 않기 위해 사용 
```java
interface Printable{
  void print(String doc);
  default void printCMYK(String doc) { } // 이미 선언하고 정의된 것처럼 되어 필요할 때만 override해서 사용
}
```

- 인터페이스의 static 메소드
  - 클래스의 static 메소드 호출 방법과 같다.
```java
interface Printable{
  static void printLine(String doc) {
    System.out.println(str);
  }
  
  default void print(String doc) {
    printLine(doc); // 인터페이스의 static 메소드 호출
    }
  }
  
  p.print() 
  Printable.printLine() // static 메소드 호출
```
- 상속 받은 것에 대해서도 instanceof 연산 된다.
```java
interface Printable{
  void printLine(String str);
}
class SimplePrinter implements Printable {...}
class MultiPrinter extends SimplePrinter {...}

public static void main(String[] args){
  Printable prn1 = new SimplePrinter();
  Printable prn2 = new Mulitrinter();
  
  if(prn1 instanceof Printable) // true
  if(prn2 instanceof Printable) // true  

## 추상클래스
- 추상 클래스 대상으로는 인스턴스 생성 불가, 참조변수 선언은 가능
