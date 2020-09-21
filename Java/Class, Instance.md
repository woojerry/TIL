## Class
 - 클래스 = 데이터 + 기능 
 - 인스턴스화 : 클래스 -> 객체(인스턴스)
 - 인스턴스를 가리키는 것을 참조변수라 한다.
 - 일반적으로 인스턴스의 데이터가 아닌 **메소드** 를 접근한다.

```java
 class BankAccount{
   // 인스턴스 변수 : 클래스 내에 선언된 변수
   String accNumber;
   String ssNumber;
   int balance = 0;

   // 인스턴스 메소드 : 클래스 내에 정의된 메소드 
   public int deposit(int amount){
    balance += amount;
    return balance;
   }
   public int withdraw(int amount){
    balance -= amount;
    return balance;
   }
   public int checkMyBalance(){
    System.out.println("잔액 : " + balance);
    return balance;
   }
 }
 
 class BankAccount00{
   public static void main(String args[]){
    // 두개의 인스턴스 생성. 여기서 woo와 park은 참조변수
    BankAccount woo = new BankAcoount();
    BankAccount park = new BankAcoount();

    // 각 인스턴스로 예금을 진행
    woo.deposit(5000);
    park.deopsit(5000);

    // 각 인스턴스 대상으로 잔액 조회
    woo.checkMyBalance();
    park.checkMyBalance();
    }
  }
  ```
  
  ## 참조변수의 특성
   ```java
   BankAccount woo = new BankAccount();
   woo = new BankAccount
   // 이 경우에는 woo가 새로운 인스턴스 참조 -> 원래 할당된 메모리는 JVM의 Garbage Collector가 자동으로 버려줌.
   
   BankAccount ref1 = new BankAcoount();
   BankAccount ref2 = ref1; // 같은 인스턴스 참조
   
   ```java
   class DupRef{
    publuc statuc void main(String[] args){
      BankAccount ref1 = new BankAccount();
      BankAccount ref2 = ref1;
      
      ref1.deposit(3000);
      ref2.deposit(2000);
      ref1.checkMyBalance();
      ref2.checkMyBalance(); // 동일한 5000 값이 나온다
      }
   ``` 
   
   ## 생성자
   ```java
    class BankAccount{
   String accNumber;
   String ssNumber;
   int balance;
   
   public BankAccount(String acc, String ss, int bal){ // 생성자
    accNumber = acc;
    ssNumber = ss;
    balance = bal;
    }
    ...
   publuc statuc void main(String[] args){
    BankAccount woo = new BankAccount("12-34-89","99999-999999",10000);
    ...}
  ```
    

   
   
  
 
