## Observer Pattern

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
