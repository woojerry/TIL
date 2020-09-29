## String Class

 - 문자열 생성 방법 두가지
 ```java
 String str1 = "Simple String"; // 
 String str2 = new String("Simple String"); 
 ```
 
 - 문자열 연결시키기
    - ```concat()``` 
    
    ```java
   class StringConcat {
    public static void main(String args[]) {
       String st1 = "Coffee";
       String st2 = "Bread";

       String st3 = st1.concat(st2);
       System.out.println(st3); // CoffeeBread
   ``` 
 
- 문자열 일부 추출
  - ```substring()```
 
   ```java
    String str = "abcdefg";
    str.substring(2); // 인덱스 2이후부터 반환 cdefg 
    str.substring(2,4); // index 2~3 위치한 문자열 반환 cd
    ```

- 문자열의 내용 비교
  - ```equals()``` // 단순 비교 true, false 반환
  - ```compareTop()``` // 앞에꺼 빼기 뒤에꺼 같으면 0반환, 다르면 연산값 반환
  - ```compareToIgnoreCase()``` // 대소문자 구분X 같으면 0 반환
  
- 기본자료형의 값 문자열로 바꾸기
  - ```valueOf()```
  
  ```java
  double e = 2.7181;
  String se = String.valueOf(e);
  ```
- 문자열 붙이기 
  - 문자열 +연산 
  ```java
  String str = "funny";
  str += "camp";  // str = str.concat("camp"); 컴파일러 자동 변환 
  // str = funnycamp
  ``` 
  
  - 문자열 + 기본자료형
  ```java 
  String str = "age: " + 17; // String str = "age: ".concat(String.valueOf(17));
  // str = age: 17
  ```
  
  - StringBuilder
  ```java
  StringBuilder stbuf = new StringBuilder("123");
  
  stbuf.append(45678); // 문자열 덧붙이기 12345678
  stbuf.delete(0, 2); // 문자열 일부 삭제 345678
  stbuf.replace(0, 3, "AB"); // 문자열 일부 교체 AB678
  stbuf.reverse(); // 문자열 내용 뒤집기 876BA
  stbuf.substring(2, 4); // 6B
  ```
  
  
  
  
