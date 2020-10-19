![p2](https://user-images.githubusercontent.com/50645183/96106604-5d10a080-0f16-11eb-9f6b-48d1a8556a93.jpg)
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

![p2](https://user-images.githubusercontent.com/50645183/96112846-39e9ef00-0f1e-11eb-99c6-bcc0ca00a7d6.PNG)


```java
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

<hr>

```java
public class NYPizzaStore extends PizzaStore {
 
	protected Pizza createPizza(String item) {
		Pizza pizza = null;
		PizzaIngredientFactory ingredientFactory = 
			new NYPizzaIngredientFactory();
 
		if (item.equals("cheese")) {
  
			pizza = new CheesePizza(ingredientFactory);
			pizza.setName("New York Style Cheese Pizza");
  
		} else if (item.equals("veggie")) {
 
			pizza = new VeggiePizza(ingredientFactory);
			pizza.setName("New York Style Veggie Pizza");
 
		} else if (item.equals("clam")) {
 
			pizza = new ClamPizza(ingredientFactory);
			pizza.setName("New York Style Clam Pizza");
 
		} else if (item.equals("pepperoni")) {

			pizza = new PepperoniPizza(ingredientFactory);
			pizza.setName("New York Style Pepperoni Pizza");
 
		} 
		return pizza;
	}
}
```
