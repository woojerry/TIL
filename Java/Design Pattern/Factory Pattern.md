## Factory Pattern

```java
Pizza orderPizza() {
  Pizza pizza = new Pizza();
  
  pizza.prepare();
  pizza.bake();
  pizza.cut();
  pizza.box();
  return pizza;
}
```
- 피자 주문 코드 -> 하지만 다른 종류의 피자를 나타낼 수 없다.

```java
Pizza orderPizza(String type) {
  Pizza pizza;
  
  if(type.euqals("cheese")) {
    pizza = new ChessePizza();
  } else if (type.equals("greek")) {
    pizza = new GreekPizza();
  } else if (type.equals("pepperoni")) {
    pizza = new PepperoniPizza();
  }
  ...
  }
```  
  
- 하지만 이 경우에도 새로운 피자가 추가될 때 상위 클래스에 영향을 받는다.
- -> Factory화 : 별도의 클래스에 만들어준다.(생산하는 공장을 만든다) 그 별도의 클래스만 수정하면 된다.(공장 구조만 바뀌면 된다)
- Factory 구현 방법 2가지
  - Factory Class
  - Factory Method

### Factory Class
```java
public class SimplePizzaFactory {//** // 피자 종류가 바뀌더라도 이 클래스만 바뀐다

	public Pizza createPizza(String type) {
		Pizza pizza = null; 

		if (type.equals("cheese")) {
			pizza = new CheesePizza();
		} else if (type.equals("pepperoni")) {
			pizza = new PepperoniPizza();
		} else if (type.equals("clam")) {
			pizza = new ClamPizza();
		} else if (type.equals("veggie")) {
			pizza = new VeggiePizza();
		}
		return pizza; // 넘겨줄 때 Pizza type으로 return
	}
}
```

```java
public class PizzaStore {
	SimplePizzaFactory factory;
 
	public PizzaStore(SimplePizzaFactory factory) { // main에서 factory 넘기면 SimplePizzaFactory형으로 받음
		this.factory = factory;
	}
 
	public Pizza orderPizza(String type) { // 피자를 주문하면
		Pizza pizza;
 
		pizza = factory.createPizza(type); // 팩토리에게 createPizza호출
                                          // Pizza type 받음
		pizza.prepare();
		pizza.bake();
		pizza.cut();
		pizza.box();

		return pizza;
	}
  // other methods here
}
```
```java
public static void main(String[] args) {
		SimplePizzaFactory factory = new SimplePizzaFactory();
		PizzaStore store = new PizzaStore(factory);

		Pizza pizza = store.orderPizza("cheese");
		System.out.println("We ordered a " + pizza.getName() + "\n"); // We ordered a cheese Pizza
		System.out.println(pizza);
```    

### Factory Method
