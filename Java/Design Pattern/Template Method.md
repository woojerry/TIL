## Template Method
> 뼈대는 위에서 정의 달라지는 부분은 하위에서 정의해, 전체적인 알고리즘 유지

- 커피와 티를 만드는 알고리즘은 다 다르지 않고 일부분은 비슷하다.

![t1](https://user-images.githubusercontent.com/50645183/101896383-458b2680-3bec-11eb-9aa7-c241da234b15.PNG)

```java
public abstract class CaffeineBeverage { // 추상 메소드
  
	final void prepareRecipe() {
		boilWater();
		brew();
		pourInCup();
		addCondiments();
	}
 
	abstract void brew(); // 제조 방법이 다른 부분은 하위클래스에서 직접 구현
  
	abstract void addCondiments(); // 제조 방법이 다른 부분은 하위클래스에서 직접 구현
 
	void boilWater() {
		System.out.println("Boiling water");
	}
  
	void pourInCup() {
		System.out.println("Pouring into cup");
	}
```
```java
public class Coffee extends CaffeineBeverage {
	public void brew() {
		System.out.println("Dripping Coffee through filter");
	}
	public void addCondiments() {
		System.out.println("Adding Sugar and Milk");
	}
}
```
```java
public class Tea extends CaffeineBeverage {
	public void brew() {
		System.out.println("Steeping the tea");
	}
	public void addCondiments() {
		System.out.println("Adding Lemon");
	}
}
```
<hr>
