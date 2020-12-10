## Adapter Pattern

- Duck에서 Turkey가 추가. Client입장에선 TurkeyAdapter를 통해 Turkey도 Duck처럼 보이도록 한다.

![adaa](https://user-images.githubusercontent.com/50645183/101759694-40ab7180-3b1d-11eb-8b92-5b7f7b02e3ce.PNG)


```java
public class TurkeyAdapter implements Duck { 
	Turkey turkey; // Turkey를 갖고 있는다.
 
	public TurkeyAdapter(Turkey turkey) {   
		this.turkey = turkey;
	}
    
	public void quack() {
		turkey.gobble();
	}
  
	public void fly() {
		for(int i=0; i < 5; i++) {
			turkey.fly();
		}
	}
}
```
```java
public class DuckTestDrive { // Client
	public static void main(String[] args) {
		MallardDuck duck = new MallardDuck();
 
		WildTurkey turkey = new WildTurkey();
		Duck turkeyAdapter = new TurkeyAdapter(turkey); // ** TukeyAdapter가 Duck형
   
		System.out.println("The Turkey says...");
		turkey.gobble();
		turkey.fly();
 
		System.out.println("\nThe Duck says...");
		testDuck(duck);
  
		System.out.println("\nThe TurkeyAdapter says...");
		testDuck(turkeyAdapter);
	}
 
	static void testDuck(Duck duck) { // 다 Duck으로 인식해서
		duck.quack(); // Quack할 때도 Turkey여도 Duck인지 Turkey인지 모른다. 
		duck.fly();
	}
}
```
- Enumeration도 iterator로 adapter를 통해 사용된다.

![Enum](https://user-images.githubusercontent.com/50645183/101763160-c03b3f80-3b21-11eb-8222-3acefa1d0e85.PNG)
