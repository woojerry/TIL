## State Pattern
> 상태에 따라 행위를 달리해야 하는 경우에 사용하는 패턴
> 어떤 Object에게 내부 상태가 변했을 때, 그것에 따른 행동도 변하게 할 수 있게 하는 패턴

## 바뀌기 전
> 새로운 상태가 들어왔을 때, 프로그램 유지보수가 어렵다.
```java
package headfirst.state.gumball;

public class GumballMachine {
 
	final static int SOLD_OUT = 0;
	final static int NO_QUARTER = 1;
	final static int HAS_QUARTER = 2;
	final static int SOLD = 3;
 
	int state = SOLD_OUT;
	int count = 0;
  
	public GumballMachine(int count) {
		this.count = count;
		if (count > 0) {
			state = NO_QUARTER;
		}
	}
  
	public void insertQuarter() {
		if (state == HAS_QUARTER) {
			System.out.println("You can't insert another quarter");
		} else if (state == NO_QUARTER) {
			state = HAS_QUARTER;
			System.out.println("You inserted a quarter");
		} else if (state == SOLD_OUT) {
			System.out.println("You can't insert a quarter, the machine is sold out");
		} else if (state == SOLD) {
        	System.out.println("Please wait, we're already giving you a gumball");
		}
	}

	public void ejectQuarter() {
		if (state == HAS_QUARTER) {
			System.out.println("Quarter returned");
			state = NO_QUARTER;
		} else if (state == NO_QUARTER) {
			System.out.println("You haven't inserted a quarter");
		} else if (state == SOLD) {
			System.out.println("Sorry, you already turned the crank");
		} else if (state == SOLD_OUT) {
        	System.out.println("You can't eject, you haven't inserted a quarter yet");
		}
	}
  
// 손잡이 돌리기 
// 캡슐 꺼내기

```

## 패턴 적용 후
> 상태를 코드 -> 클래스화 , 각각의 상태를 하나의 인터페이스 밑에 두어 관리  
> 상태에 따른 함수에서 다른 상태로 setState를 바꿔주기도 한다.


![state](https://user-images.githubusercontent.com/50645183/100464886-bd981d80-3111-11eb-8780-bb9b3db7fae6.PNG)




```java
public interface State {
 
	public void insertQuarter();
	public void ejectQuarter();
	public void turnCrank();
	public void dispense();
}

```

```java
public class GumballMachine {
 
	State soldOutState;
	State noQuarterState;
	State hasQuarterState;
	State soldState;
 
	State state = soldOutState; // GumballMachine의 처음 상태 설정
	int count = 0;
 
	public GumballMachine(int numberGumballs) {
		soldOutState = new SoldOutState(this); // 각각의 상태 가리킴 
		noQuarterState = new NoQuarterState(this);
		hasQuarterState = new HasQuarterState(this);
		soldState = new SoldState(this);

		this.count = numberGumballs;
 		if (numberGumballs > 0) {
			state = noQuarterState;
		} 
	}
 
	public void insertQuarter() {
		state.insertQuarter(); // 직접 하는 것이 아닌 각각의 상태에 따른 insertQuarter를 한다.
	}
 
	public void ejectQuarter() {
		state.ejectQuarter();
	}
 
	public void turnCrank() {
		state.turnCrank();
		state.dispense();
	}

	void setState(State state) {
		this.state = state;
	}
 
	void releaseBall() {
		System.out.println("A gumball comes rolling out the slot...");
		if (count != 0) {
			count = count - 1;
		}
	}
 
	int getCount() {
		return count;
	}
 
	void refill(int count) {
		this.count = count;
		state = noQuarterState;
	}

    public State getState() {
        return state; // 현재 상태 리턴
    }

    public State getSoldOutState() {
        return soldOutState;
    }

    public State getNoQuarterState() {
        return noQuarterState;
    }

...

```

```java
public class NoQuarterState implements State {
    GumballMachine gumballMachine;
 
    public NoQuarterState(GumballMachine gumballMachine) {
        this.gumballMachine = gumballMachine;
    }
 
	public void insertQuarter() {
		System.out.println("You inserted a quarter");
		gumballMachine.setState(gumballMachine.getHasQuarterState()); // gumballMachine의 상태 바꿔줌
	}
 
	public void ejectQuarter() {
		System.out.println("You haven't inserted a quarter");
	}
 
	public void turnCrank() {
		System.out.println("You turned, but there's no quarter");
	 }
 
	public void dispense() {
		System.out.println("You need to pay first");
	} 
 
 ```

참고 <https://lee1535.tistory.com/100>

