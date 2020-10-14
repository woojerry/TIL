## Observer Pattern
![캡처](https://user-images.githubusercontent.com/50645183/95947480-a9ca7d80-0e29-11eb-91cc-ddb4866d2514.PNG)

여러개의 display device에 뿌려주기 위한 Weather data object를 만듦


```java
public class WeatherData { // 원래 코드
  // insatnce variable declarations
  
  public void measuermentsChanged() {
    float temp = getTemprature();
    float humidity = getHumidity();
    float pressure = getPressure();
    
    currentConditionsDisplay.update(temp, humidity, pressure);
    statisticsDisplay.update(temp, humidity, pressure);
    forecastDisplay.update(temp, humidity, pressure);
    
    // other WeatherData methods here
}
```
- 이 경우에는 새로운 Display device가 추가 됐을 때 일일히 추가해줘야하는 번거로움이 있다. -> Observer가 필요
![weather2](https://user-images.githubusercontent.com/50645183/95955773-557aca00-0e38-11eb-8d85-4ae6ab6f0c76.PNG)

```java
public class WeatherData implements Subject { // Subject
  private ArrayList observers; // ArrayList -> Array의 크기 수시로 변경 가능
  private float temperature;
  private float humidity;
  private float pressure;
  
  public WeatherData() {
    observers = new ArrayList(); // observer에 ArrayList생성
  }
  
  public void registerObserver(Observer o) {
    observers.add(o);
  }
  
  public void removeObserver(Observer o) {
    int i = observers.indexOf(o);
    if (i >= 0) { // index 값에 observer가 있으면
    observers.remove(i);
    }
  }
  
  public void notifyObservers() {
    for (int i = 0; i < observers.size(); i++) {
      Observer observer = (Observer)observers.get(i); // Observer형으로 가져옴 
      observer.update(temperature, humidity, pressure);
    }
  }
  
  public void measurementsChanged() { // 한줄로 바뀜
    notifyObservers();          // display 장치가 추가 되더라도 코드 바뀔 필요X
  }
  
  public void setMeasurements(float temperature, float humidity, float pressure) {
    this.temperature = temperature;
    this.humidity = humidity;
    this.pressure = pressure;
    measurementsChanged();
  }
  
  public float getTemperature() { return temperature; }
  public float getHumidity() { return humidity; }
  public float getPressure() { return pressure; }
}
```
```java
public interface Observer {
  public void update(float temp, float humidity, float pressure);
}
```
```java
public class CurrentConditionsDisplay implements Observer, DisplayElement {
  private float temperature;
  private float humidity;
  private Subject weatherData;
  
  public CurrentConditionsDisplay(Subject weatherData) { // 가입하고 싶은 Subject -> weatherData 
    this.weatherData = weatherData;
    weatherData.registerObserver(this);
  }
  
  public void update(float temperature, float humidity, float pressure) {
    this.temperature = temperature;
    this.humidity = humidity;
    display(); // Not very good to call display() inside of update(). See MVC
  }
  
  public void display() {
    System.out.println("Current conditions: " + temperature + "F degrees and " + humidity + "% humidity");
  }
}
```




 
