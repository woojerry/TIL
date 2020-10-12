## Strategy Pattern
  - 디자인 원칙 1 : 달라지는 부분을 찾아내고, 달라지지 않는 부분으로부터 분리 시킴. 
  - 디자인 원칙 2 : 구현이 아닌 인터페이스에 맞춰서 프로그래밍 (Program to an interface, not an implementation)
![InkedInkedduck2_LIdd](https://user-images.githubusercontent.com/50645183/95763466-06bf1a00-0cea-11eb-82eb-560a7c2427b3.jpg)
  - 유지보수를 위해 변하는 부분은 has-a관계가 좋다. 재사용할 때 상속보다는 합성이 좋다. (상속은 불변하므로, 자식 클래스가 다 영향 받으므로)

```java
public abstract class Duck {
  FlyBehavior flyBehavior;
  QuackBehavior quackBehavior;
  
  public Duck() {
  }
  
  public abstract void display(); // Duck 종류마다 다르므로 override해서 사용
  
  public void performFly() {
    flyBehavior.fly(); // flyBehavior의 fly호출
  }
  
  public void performQuack() {
    quackBehavior.quack();
  }
  
  public void setFlyBehavior(FlyBehavior fb) {
    flyBehavior = fb;
  }
  
  public void setQuackBehavior(QuackBehavior qb) {
    quackBehavior = qb;
  }
  
  public void swim() {
    System.out.println("All ducks float, even decoys!");
  }  
}
```
```java
public interface FlyBehavior { // Duck과 has-a 관계  
  public void fly();
}
```
```java 
public class FlyWithWings implements FlyBehavior {
  public void fly() {
    System.out.println("I'm flying!!");
  }
}
```
```java
public class FlyNoWay implements FlyBehavior {
  public void fly() {
    System.out.println("I can't fly.");
  }
}
```
```java
public class MallardDuck extends Duck { // Duck과 is-a 관계. 상속
  public MallardDuck() { // 생성자에서 Duck의 특성 나타냄
    quackBehavior = new Quack();
    flyBehavior = new FlyWithWings(); // flybehavior는 Flybehavior형
  }
  
  public void display() { // display만 override
    System.out.println("I'm a real Mallard duck");
  }
}
```
```java
public class ModelDuck extends Duck { 
  public ModelDuck(){
    flyBehavior = new FlyNoWay(); // Duck의 다른 특성
    quackBehavior = new Quack();
  }
  
  public void display() {
    System.out.println("I'm a model duck");
  }
}
```
