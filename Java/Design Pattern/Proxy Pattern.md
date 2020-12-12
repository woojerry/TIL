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
1. Remote Interface 설계 (외부에 제공되는 서비스에 대해 interface 
2. Remote Implementation 
3. generate stub(client쪽의 proxy), skeleton(service쪽 proxy) using rmic
4. start the RMI registry
5. start the remote service

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

```java
import java.rmi.*;   
import java.rmi.server.*; // UnicastRemoteObject가 들어 있다.
public class MyRemoteImpl extends UnicastRemoteObject implements MyRemote {
    public String sayHello( ) {
       return “Server says, ‘Hey’”;
    }
    public MyRemoteImple( ) throws RemoteException { }
    public static void main(String[ ] args) {
       try {
	   MyRemote service = new MyRemoteImpl( );
	   Naming.rebind(“RemoteHello”, service);  //rmiregistry에 결합시킴
       } catch (Exception ex) {
	   ex.printStackTrace();
    }   
  }   
}
```

