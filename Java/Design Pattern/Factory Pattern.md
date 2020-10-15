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

![p2](https://user-images.githubusercontent.com/50645183/96106604-5d10a080-0f16-11eb-9f6b-48d1a8556a93.jpg)

- PizzaStore클래스에서는 만들어진 어떤 종류의 Pizza이던 Pizza클래스로 보인다.
- SimplePizzaFactory는 생성만 하기위한 클래스라 createPizza() 메소드만 갖고 있다.


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
 
	public PizzaStore(SimplePizzaFactory factory) { // main에서 factory 넘기면 SimplePizzaFactory형으로 받음 ??
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

- NYStyle Pizza와 ChicagoPizza가 있다.
- 별도의 클래스 없이 다형성을 이용해 메소드 오버라이딩을 통해 사용

![p2](https://user-images.githubusercontent.com/50645183/96112846-39e9ef00-0f1e-11eb-99c6-bcc0ca00a7d6.PNG)

![p3](https://user-images.githubusercontent.com/50645183/96113019-7ae20380-0f1e-11eb-89e0-6ef250de4ad9.PNG)

```java
public static void main(String[] args) {
	PizzaStore nyStore = new NYPizzaStore();
	PizzaStore chicagoStore = new ChicagoPizzaStore();
	
Pizza pizza = nyStore.orderPizza("cheese"); // order 했을 때 NYPizzaStore의 orederPizza호출
	System.out.println("Ethan ordered a " + pizza.getName() + "\n");
 
	pizza = chicagoStore.orderPizza("cheese");
	System.out.println("Joel ordered a " + pizza.getName() + "\n");
```
```java
package headfirst.factory.pizzafm;

public abstract class PizzaStore {
 
	abstract Pizza createPizza(String item); // abstract
 
	public Pizza orderPizza(String type) {
		Pizza pizza = createPizza(type); // createPizza는 다형성에 의해 NYPizzaStore의 메소드로
		System.out.println("--- Making a " + pizza.getName() + " ---");
		pizza.prepare();
		pizza.bake();
		pizza.cut();
		pizza.box();
		return pizza;
	}
}
```
```java
public class NYPizzaStore extends PizzaStore { // 하지만 여기에는 orderPizza 없으므로
						// Pizza Store의 orderPizza로
	Pizza createPizza(String item) { // **
		if (item.equals("cheese")) {
			return new NYStyleCheesePizza();
		} else if (item.equals("veggie")) {
			return new NYStyleVeggiePizza();
		} else if (item.equals("clam")) {
			return new NYStyleClamPizza();
		} else if (item.equals("pepperoni")) {
			return new NYStylePepperoniPizza();
		} else return null;
	}
}
```
```java
public class ChicagoPizzaStore extends PizzaStore {

	Pizza createPizza(String item) { // **
        	if (item.equals("cheese")) {
            		return new ChicagoStyleCheesePizza();
        	} else if (item.equals("veggie")) {
        	    	return new ChicagoStyleVeggiePizza();
        	} else if (item.equals("clam")) {
        	    	return new ChicagoStyleClamPizza();
        	} else if (item.equals("pepperoni")) {
            		return new ChicagoStylePepperoniPizza();
        	} else return null;
	}
}
```

