## Decorator Pattern
- 커피에 토핑이나 우유 등을 추가할 때마다 클래스의 개수가 폭발적으로 증가
![coffe](https://user-images.githubusercontent.com/50645183/95971815-a85e7c80-0e4c-11eb-805d-1db814965b18.PNG)

- 그래서 나온 해결책 -> 인스턴스 변수와 슈퍼 클래스의 상속을 사용

![c2](https://user-images.githubusercontent.com/50645183/95972454-6e41aa80-0e4d-11eb-8b29-4006b667c73a.PNG)

- 하지만 첨가물 바뀌거나 이럴 때 슈퍼클래스 수정해야함.(상위클래스가 바뀌면 영향을 너무 많이 준다)변하는 부분은 따로 띄어서 하는게 좋다 

```java
public class Beverage {
// declare instances variables for milkCost, soyCost ...

public float cost() { // 종류 바뀔 때마다 코드가 바뀌어야한다.
  float condimentCost = 0.0;
  if (hasMilk()){
    condimentCost += milkCost;
  }
  if (hasSoy()) {
    condimentCost += soyCost;
  }
  if (hasMocha()) {
    condimentCost += mochaCost;
  }
  ...
  return condimentCost;
  }
}
```

- Classes should be open for extension, but closed for modification. 변경 X, 추가 O
- Decorator Pattern 사용.
- Java I/O, Python도 이와 비슷

![c3](https://user-images.githubusercontent.com/50645183/95977027-4bb29000-0e53-11eb-8844-6f57940ae172.PNG)

![c4](https://user-images.githubusercontent.com/50645183/95977245-99c79380-0e53-11eb-9e06-09fbf9830db9.PNG)



```java
public abstract class Beverage {
  String description = "Unknown Beverage";
  
  public String getDescription() {
    return description;
  }
  
  public abstract double cost();
}
```
```java
public class DarkRoast extends Beverage {
  public DarkRoast() {
    description = "Dark Roast Coffee";
  }
  
  public double cost() {
    return .99;
  }
}

public class Espresso extends Beverage {
  public Espresso() {
    description = "Espresso";
  }
  
  public double cost() {
    return 1.99;
  }
}
```
```java
public abstract class CondimentDecorator extends Beverage {
  public abstract String getDescription();
}
```
```java
public class Milk 


