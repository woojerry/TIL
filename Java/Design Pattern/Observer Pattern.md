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
![weather](https://user-images.githubusercontent.com/50645183/95947398-7daefc80-0e29-11eb-8041-766f676cceea.PNG)

 
