## Iterator Pattern

## Array vs ArrayList
- Array는 size를 한번 정하면 바꿀 수 없다. (fixed), ArrayList는 size가 자유자재다 (variable).
- Array는 .length / ArrayList는 .size로 가져온다
- 둘다 순서대로가 아닌 원하는 부분에 바로 접근 가능
![array](https://user-images.githubusercontent.com/50645183/100516327-7e77d400-31c6-11eb-9d77-6e80591de8ad.PNG)

![List](https://user-images.githubusercontent.com/50645183/100517822-f3e8a200-31d0-11eb-903f-60fe97490602.PNG)

- Collection에서 상위 interface가 List에 해당하는 것들은 Iterator를 호출하면 Iterator를 return한다.
  - ArrayList는 List고, List는 Collection , Collection이면 iterable이므로 iterable의 .iterator를 호출하면 순차적으로 access한다.
  - ``` hasNext(), next(), remove()``` 사용 가능


- 아침메뉴인 pancake는 ArrayList로 되어있고, 저녁메뉴는 array로 되어있다. 이걸로 통합 메뉴판을 만들려고 한다. -> iterator 사용 but
  배열에 대해서는 iteator가 없으므로 **직접** 만들어야한다.
    - ```hasNetxt(), next()```만 구현
    - 각각의 메뉴에서 Iterator를 implement하고, 각각 createIterator() 생성한다.
    

```java
public interface Iterator {
	boolean hasNext();
	Object next();
}
```
```java
public class DinerMenuIterator implements Iterator {
  
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
