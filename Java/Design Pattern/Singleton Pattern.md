## Singleton Pattern
> 인스턴스가 하나 뿐인 특별한 객체를 만들 수 있게 해주는 패턴
- 객체가 전체 프로그램에서 오직 **하나만** 생성되어야 하는 경우에 사용

```java
public class Singleton {
	private static Singleton uniqueInstance; // static -> 클래스 변수로
                                           // private static이므로 선언된 클래스 내부에서만 접근 가능
	// other useful instance variables here 
 
	private Singleton() {}  // 밖에서 Singleton s = new Singleton(); 이렇게 호출 불가
                          // Singleton s = SIngleton.getInstance(); 이렇게 해야한다
	public static Singleton getInstance() {
		if (uniqueInstance == null) { // 처음 선언했을 떄는 null
			uniqueInstance = new Singleton(); // 없다면 Singleton 하나 생성
		}
		return uniqueInstance;  // null이 아닐 때는 만들어진 것 return
	}
 
	// other useful methods here
}
```

```java
public class Singleton {
	private static Singleton uniqueInstance;
 
	// other useful instance variables here
 
	private Singleton() {}
 
	public static synchronized Singleton getInstance() { // synchronized로 멀티스레딩 문제 해결
		if (uniqueInstance == null) {
			uniqueInstance = new Singleton();
		}
		return uniqueInstance;
	}
 
	// other useful methods here
}
```
```java
public class Singleton {
	private static Singleton uniqueInstance;
 
	private Singleton() {}
 
	public static Singleton getInstance() {
		if (uniqueInstance == null) {
			synchronized (Singleton.class) {
				if (uniqueInstance == null) {
					uniqueInstance = new Singleton();
				}
			}
		}
		return uniqueInstance;
	}
}
```
