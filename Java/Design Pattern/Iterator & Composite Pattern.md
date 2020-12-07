

## Array vs ArrayList
- Array는 크기를 한번 정하면 바꿀 수 없다. (fixed), ArrayList는 크기가 자유자재다 (variable).
- 크기를 Array는 .length / ArrayList는 .size로 가져온다
- 둘다 순서대로가 아닌 원하는 부분에 바로 접근 가능
![array](https://user-images.githubusercontent.com/50645183/100516327-7e77d400-31c6-11eb-9d77-6e80591de8ad.PNG)

![List](https://user-images.githubusercontent.com/50645183/100517822-f3e8a200-31d0-11eb-903f-60fe97490602.PNG)

- Collection에서 상위 interface가 List에 해당하는 것들은 Iterator를 호출하면 Iterator를 return한다.
  - ArrayList는 List고, List는 Collection , Collection이면 iterable이므로 iterable의 .iterator를 호출하면 순차적으로 access한다.
  - ``` hasNext(), next(), remove()``` 사용 가능

## Iterator Pattern
> 어떤 자료형이던(List, ArrayList, Array이던 내부 구조에 관계없이) hasNext(), next()( remove())만으로 데이터를 순차적으로 처리하겠다. 

- 아침메뉴인 pancake는 ArrayList로 되어있고, 저녁메뉴는 array로 되어있다. 이걸로 통합 메뉴판을 만들려고 한다. -> iterator 사용 but
  배열에 대해서는 iteator가 없으므로 **직접** 만들어야한다.
    - ```hasNetxt(), next()```만 구현
    - 각각의 메뉴에서 Iterator를 implement하고, 각각 createIterator() 생성한다.
    - 데이터를 접근할 때, Waitress가 Iterator를 통해 이루어진다. 
    
![iterator](https://user-images.githubusercontent.com/50645183/100535527-204a0000-325d-11eb-8f24-f68a88b09550.PNG)
    
  
```java
public interface Iterator {
	boolean hasNext();
	Object next();
}
```
```java
public class DinerMenu implements Menu {
  static final int MAX_ITEMS = 6;
  int numberOfItems = 0;
  MenuItem[] menuItems;
  ...
 
  public Iterator createIterator() { // Diner Menu에 새로 생김
      return new DinerMenuIterator(menuItems);
  }
} 
```
```java
public class PancakeHouseMenu implements Menu {
  public Iterator createIterator() { // Pancake Menu에 새로 생김
      return new PancakeHouseMenuIterator(menuItems);
  }
}
```
```java
public class Waitress {
  
  ...
  public void printMenu() { 
      Iterator pancakeIterator = pancakeHouseMenu.createIterator();
      Iterator dinerIterator = dinerMenu.createIterator();

      System.out.println("MENU\n----\nBREAKFAST");
      printMenu(pancakeIterator);
      System.out.println("\nLUNCH");
      printMenu(dinerIterator);
  }
  private void printMenu(Iterator iterator) {
      while (iterator.hasNext()) {
        MenuItem menuItem = (MenuItem)iterator.next();
        System.out.print(menuItem.getName() + ", ");
        System.out.print(menuItem.getPrice() + " -- ");
        System.out.println(menuItem.getDescription());
		}
  }
}
```  

- 그리고 Java에서 제공하는 Iterator util을 써서 하는 방법을 사용한다면 Iterator가 3가지 메소드를 갖고 있으므로
  remove까지 implements하면서 만들어줘야 한다.
 
- 





- 클래스를 바꾸는 이유는 한 가지 뿐이어야 한다. 
	- 클래스를 고치는 것은 최대한 피해야 한다. 코드를 변경하다 보면 온갖 문제가 생겨날수 있으니까..
	
	- 때문에 코드를 변경할 만한 이유가 두가지가 되면 그만큼 그 클래스를 나중에 고쳐야 할 가능성이 커지게 될 뿐 아니라, 디자인에 있어서 	       이 동시에 영향이 미치게 된다. 이 원칙에 따르면 한 역할은 한 클래스에서만 맡게 해야 한다.



출처: https://jusungpark.tistory.com/25 [정리정리정리]
<hr>

## CafeMenu까지 추가 됐을 때,
> CafeMenu는 Hashtable의 자료형, key/MenuItem 중 MenuItem가져와 Iterator로 통합해 사용

![collection22](https://user-images.githubusercontent.com/50645183/100579710-075a5100-3328-11eb-9abc-90f5a11f5111.jpg)



- Collection에 속하는 것들은 다 iterator 사용 가능. (array, 즉 배열은 직접 구현해줘야한다)
- Map은 아니다.
	- map.keySet()이 리턴하는 게 set -> Collection

<hr>
## Composite Pattern
> recursive한 자료구조에 사용. Tree Structrue처럼 계층구조를 가지고 있는 모든 object들을 동일시하게 하는 패턴.

![composite](https://user-images.githubusercontent.com/50645183/101358515-4e26e880-38de-11eb-92fc-80870b7ec7ea.PNG)
- 
- print될 때 각각 클래스에서 자기 자신을 print하고, child에 있는것도 print한다.

```java
public abstract class MenuComponent {
   
	public void add(MenuComponent menuComponent) { // MenuComponent가 들어감
		throw new UnsupportedOperationException();
	}
	public void remove(MenuComponent menuComponent) { // MenuComponent가 들어감
		throw new UnsupportedOperationException();
	}
	public MenuComponent getChild(int i) {
		throw new UnsupportedOperationException();
	}
  
	public String getName() {
		throw new UnsupportedOperationException();
	}
	public String getDescription() {
		throw new UnsupportedOperationException();
	}
	public double getPrice() {
		throw new UnsupportedOperationException();
	}
	public boolean isVegetarian() {
		throw new UnsupportedOperationException();
	}
  
	public void print() {
		throw new UnsupportedOperationException();
	}
}
```
```java
import java.util.Iterator;
import java.util.ArrayList;

public class Menu extends MenuComponent {
	ArrayList menuComponents = new ArrayList(); // Menu에는 여러 child가 있으므로
	String name;
	String description;
  
	public Menu(String name, String description) {
		this.name = name;
		this.description = description;
	}
 
	public void add(MenuComponent menuComponent) { // 들어오고 나가는거 MenuComponent
		menuComponents.add(menuComponent);
	}
 
	public void remove(MenuComponent menuComponent) { // 들어오고 나가는거 MenuComponent	
		menuComponents.remove(menuComponent);
	}
 
	public MenuComponent getChild(int i) {
		return (MenuComponent)menuComponents.get(i);
	}
 
	public String getName() {
		return name;
	}
 
	public String getDescription() {
		return description;
	}
 
	public void print() { // print될 때 각각 클래스에서 자기 자신을 print하고, child에 있는것도 print한다.
		System.out.print("\n" + getName());
		System.out.println(", " + getDescription());
		System.out.println("---------------------");
  
		Iterator iterator = menuComponents.iterator(); // child에 있는걸 iterator로 해서
		while (iterator.hasNext()) {
			MenuComponent menuComponent = 
				(MenuComponent)iterator.next();
			menuComponent.print(); // print함 
		}
	}
}
```
```java
import java.util.Iterator;
import java.util.ArrayList;

public class MenuItem extends MenuComponent {
	String name;
	String description;
	boolean vegetarian;
	double price;
    
	public MenuItem(String name, 
	                String description, 
	                boolean vegetarian, 
	                double price) 
	{ 
		this.name = name;
		this.description = description;
		this.vegetarian = vegetarian;
		this.price = price;
	}
  
	public String getName() {
		return name;
	}
  
	public String getDescription() {
		return description;
	}
  
	public double getPrice() {
		return price;
	}
  
	public boolean isVegetarian() {
		return vegetarian;
	}
  
	public void print() { // 여기서 recursive 끝남
		System.out.print("  " + getName());
		if (isVegetarian()) {
			System.out.print("(v)");
		}
		System.out.println(", " + getPrice());
		System.out.println("     -- " + getDescription());
	}
}
```
```java
import java.util.Iterator;
  
public class Waitress { // Waitress는 allMenu 받아다가
	MenuComponent allMenus;
 
	public Waitress(MenuComponent allMenus) {
		this.allMenus = allMenus;
	}
 
	public void printMenu() { // printMenu만 하면 recursive한 구조로 모든게 print된다.
		allMenus.print();
	}
}
