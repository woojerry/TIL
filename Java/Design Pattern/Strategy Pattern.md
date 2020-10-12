## Strategy Pattern
  - 디자인 원칙 1 : 달라지는 부분을 찾아내고, 달라지지 않는 부분으로부터 분리 시킴. 
  - 디자인 원칙 2 : 구현이 아닌 인터페이스에 맞춰서 프로그래밍 (Program to an interface, not an implementation)

```java
public abstract class Duck {
  FlyBehavior flyBehavior;
  QuackBehavior quackBehavior;
  
  public Duck() {
  }
  
  public abstract void display();
  
  public void performFly() {
    flyBehavior.fly();
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
public interface FlyBehavior {
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
public class MallardDuck extends Duck {
  public MallardDuck() {
    quackBehavior = new Quack();
    flyBehavior = new FlyWithWings(); // flybehavior는 Flybehavior형
  }
  
  public void display() {
    System.out.println("I'm a real Mallard duck");
  }
}
```
