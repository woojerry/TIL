## Java 가상머신의 메모리 모델
> 메모리 공간 활용의 효율성으르 높이기 위해 메모리 공간을 3개의 영역으로 구분
    
- 메소드 영역 (Method Area) : 메소드의 바이트코드와 static 변수가 할당되는 메모리 공간
    -  이 영역에 저장된 내용은 프로그램 종료 시 소멸
    ```java
    class Boy{
      static int average = 0; // static 변수
      public void Run(){...}
    }
    
    class MyMain{
      public static void main(String args[]) {
        Boy b = new Boy(); // 인스턴스 생성
        Boy.average += 5; // 클래스 변수 접근
        ....
      }
    }
    ```
    
- 스택 영역 (Stack Area) : 지역변수, 매개변수가 할당되는 영역
    - 이 영역에 저장된 변수는 해당 변수가 선언된 메소드 종료 시 소멸
    ```java
    public static void main(String args[]) {
      int num1 = 10;
      int num2 = 20;
      adder(num1, num2);
      System.out.println("end of program");
    }
    
    public static void adder(int n1, int n2){
      int result = n1 + n2;
      return result;
    }
    ```
    
 - 힙 영역 (Heap Area) : 인스턴스가 저장되는 영역
    - Garbage Colletion의 대상이 되는 영역이다. (참조가 되는지 안되는지)
    ```java
    public static void simpleMethod(){
      String str1 = new String("My String"); // str1(스택 영역) -> My String은 인스턴스(힙 영역)
      String str2 = new String("Your String");
      ....
      str1 = null; // 참조 관계 관계가 끊어짐 -> 가비지 컬렉션의 대상이 된다
      str2 = null; // 위와 마찬가지로 참조 관계 소멸
      ...
    }
    ```
