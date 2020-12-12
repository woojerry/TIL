## Proxy Pattern
> 어떤 클래스의 객체 생성이 오래 걸리는 경우 그 일을 분업을 하여 proxy 클래스에서 처리 할 수 있는 부분은 처리를 하고 proxy 클래스에서 처리 할 수 없는 작업에 대해서만 실제 클래스의 객체를 생성하고 위임하는 방식

- GumballMonitor ----- GumballMachine 사이에 getLocation(), getCount(), getState()를 한다.
- 하지만 다른 컴퓨터에서 이를 각각 돌리려고할 때는 문제 발생 -> 새로운 방법으로 호출 필요 -> 중간 역할 Proxy
- Interface를 통해 외부에 어떤 서비스를 제공할지 알려준다.

![proxy1](https://user-images.githubusercontent.com/50645183/101979518-079c0a00-3ca1-11eb-854c-5aac205a2539.PNG)


```java
public class GumballMonitor {
	GumballMachine machine;
 
	public GumballMonitor(GumballMachine machine) {
		this.machine = machine;
	}
 
	public void report() {
		System.out.println("Gumball Machine: " + machine.getLocation());
		System.out.println("Current inventory: " + machine.getCount() + " gumballs");
		System.out.println("Current state: " + machine.getState());
	}
}
```
<hr>

## Java RMI 
> Remote Proxy
1. Remote Interface 설계 (외부에 제공되는 서비스에 대해 interface 
2. Remote Implementation 
3. generate stub(client쪽의 proxy), skeleton(service쪽 proxy) using rmic
4. start the RMI registry
5. start the remote service

![proxy2](https://user-images.githubusercontent.com/50645183/101982945-bd278700-3cba-11eb-8819-779281b09290.PNG)


### 1
```java
public interface MyRemote extends Remote { // extends Remote는 원격 서비스 표시 
  public String sayHello() throws RemoteException;
}
```

### 2,3
```java
public class MyRemoteImpl extends UnicastRemoteObject implements MyRemote { // 인터페이스에 들어있는 모든 메소드를 구현했는지 컴파일러에서 체크
    public MyRemoteImpl() throws RemoteException { } // 3
    public String sayHello() {
        return “Server says, ‘Hey’”;
    }
  // 기타 코드
}
```

### 4
```java
try {
     MyRemote service = new MyRemoteImpl( );
     Naming.rebind (“RemoteHello”, service);
} catch (Exception ex) { … }
```

```java
import java.rmi.*;   
import java.rmi.server.*; // UnicastRemoteObject가 들어 있다.
public class MyRemoteImpl extends UnicastRemoteObject implements MyRemote {
    public String sayHello( ) {
       return “Server says, ‘Hey’”;
    }
    public MyRemoteImple( ) throws RemoteException { }
    public static void main(String[ ] args) { / main에서
       try {
	   MyRemote service = new MyRemoteImpl( );
	   Naming.rebind(“RemoteHello”, service);  //rmiregistry에 결합시킴
       } catch (Exception ex) {
	   ex.printStackTrace();
    }   
  }   
}
```
```java
import java.rmi.*;  // (RMI 레지스트리 룩업을 처리하기 위한) Naming 클래스가 존재
public class MyRemoteClient {
    public static void main (String[ ] args) {
       new MyRemoteClient( ).go( );
    }
    public void go( ) {
      try {
        MyRemote service=(MyRemote)Naming.lookup(“rmi://127.0.0.1/RemoteHello”);
        String s = service.sayHello(); // stub의 sayHello(), 원격의 myRemote의 sayHello() 호출
        System.out.println(s);
      } catch (Exception ex) {
        ex.printStackTrace( );
      }
   }
}
```
<hr>

![proxy3](https://user-images.githubusercontent.com/50645183/101982960-d29cb100-3cba-11eb-994b-0551c59a9fdd.PNG)

```java
public interface GumballMachineRemote extends Remote { // 원격제어
	public int getCount() throws RemoteException;
	public String getLocation() throws RemoteException;
	public State getState() throws RemoteException;
}
```
```java
public class GumballMachine extends UnicastRemoteObject implements GumballMachineRemote {
	State soldOutState;
	State noQuarterState;
	State hasQuarterState;
	State soldState;
	State winnerState;
 
	State state = soldOutState;
	int count = 0;
 	String location;

	public GumballMachine(String location, int numberGumballs) throws RemoteException {
		soldOutState = new SoldOutState(this);
		noQuarterState = new NoQuarterState(this);
		hasQuarterState = new HasQuarterState(this);
		soldState = new SoldState(this);
		winnerState = new WinnerState(this);

		this.count = numberGumballs;
 		if (numberGumballs > 0) {
			state = noQuarterState;
		} 
		this.location = location;
	}
	public int getCount() {
		return count;
	}
 
    	public State getState() {
        return state;
    	}
 
   	 public String getLocation() {
        return location;
    	}
	
	...
	// other codes
}	
```
```java
public class GumballMonitor {
	GumballMachineRemote machine;
 
	public GumballMonitor(GumballMachineRemote machine) {
		this.machine = machine;
	}
 
	public void report() {
		try {
			System.out.println("Gumball Machine: " + machine.getLocation());
			System.out.println("Current inventory: " + machine.getCount() + " gumballs");
			System.out.println("Current state: " + machine.getState());
		} catch (RemoteException e) {
			e.printStackTrace();
		}
	}
}
```
