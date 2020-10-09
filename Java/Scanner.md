## Scanner
  - Scanner를 사용하기 위해서는 ```import java.util.Scanner;```를 통해 외부 클래스를 호출해야한다
  - Scanner 객체 생성을 해준 뒤 객체를 사용하면 된다. 
    ```java
    Scanner scanner = new Scanner(System.in); // 입력받는 부분
    ```
  - 입력 받을 Daya Type에 따라 메소드를 호출해준다.
    ```java
    int num = scanner.nextInt // 정수형
    double num = scanner.nextDouble // 실수
    String str = scanner.nextLine() // 공백을 포함한 문자열
    String str= scanner.next() // 공백을 포함하지 않는 문자열
    ```
