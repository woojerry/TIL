## Command Pattern
- Remote controller 입장에서는 다 type이 Command형으로 보인다

```java
public interface Command {
	public void execute();
}
```
```java
public class RemoteControlTest {
	public static void main(String[] args) {
		SimpleRemoteControl remote = new SimpleRemoteControl();
		Light light = new Light();
		GarageDoor garageDoor = new GarageDoor();
		LightOnCommand lightOn = new LightOnCommand(light);
		GarageDoorOpenCommand garageOpen = 
		    new GarageDoorOpenCommand(garageDoor);
 
		remote.setCommand(lightOn); // 1-1. 이걸 하면
		remote.buttonWasPressed(); // 1-3. 그리고 버튼이 눌리면 
		remote.setCommand(garageOpen); 2-1. garage
		remote.buttonWasPressed(); 2-4. 버튼 
    }
}
```

```java
public class SimpleRemoteControl {
	Command slot; 
	public SimpleRemoteControl() {}
 
	public void setCommand(Command command) { // 1-2.slot에 LightonCommand가 들어감
    slot = command;                         // 2-2.slot에 GarageDoorOpenCommand
	}
 
	public void buttonWasPressed() { 
		slot.execute(); // 1-4, 2-4. excute실행
	}
}
```

```java
public class LightOnCommand implements Command {
	Light light;

	public LightOnCommand(Light light) {
		this.light = light;
	}

	public void execute() { 
		light.on(); // 1-5. light on
	}
}
```

```java
public class GarageDoorOpenCommand implements Command {
	GarageDoor garageDoor;

	public GarageDoorOpenCommand(GarageDoor garageDoor) {
		this.garageDoor = garageDoor;
	}

	public void execute() { 
		garageDoor.up(); // 2-5. 실제로는 .up() 실행
	}
}
```

```java
public class Light {

	public Light() {
	}

	public void on() { // 1-6. 최종
		System.out.println("Light is on");
	}

	public void off() {
		System.out.println("Light is off");
	}
}
```

```java
public class GarageDoor {

	public GarageDoor() {
	}

	public void up() { // 2-6. 최종실행
		System.out.println("Garage Door is Open"); 
	}

	public void down() {
		System.out.println("Garage Door is Closed");
	}

	public void stop() {
		System.out.println("Garage Door is Stopped");
	}

	public void lightOn() {
		System.out.println("Garage light is on");
	}

	public void lightOff() {
		System.out.println("Garage light is off");
	}
}
```


