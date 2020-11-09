## Math Class
> 수학 관련 연산 기능 제공
```java
public static void main(String[] args) {
 System.out.println("원주율: " + Math.PI);
 System.out.println("2의 제곱근: " + Math.sqrt(2));
 System.out.println();
 System.out.println("파이에 대한 Degree: " + Math.toDegrees(Math.PI));
 System.out.println("2 파이에 대한 Degree: " + Math.toDegrees(2.0 * Math.PI));
 System.out.println();

 double radian45 = Math.toRadians(45); // 라디안으로의 변환!
 System.out.println("싸인 45: " + Math.sin(radian45));
 System.out.println("코싸인 45: " + Math.cos(radian45));
 System.out.println("탄젠트 45: " + Math.tan(radian45));
 System.out.println();
 System.out.println("로그 25: " + Math.log(25));
 System.out.println("2의 16승: "+ Math.pow(2, 16));
``` 

- 난수 생성
```Random rand = new Random();```
```java
 public boolean nextBoolean() // boolean형 난수 반환
 public int nextInt() // int형 난수 반환
 public long nextLong() // long형 난수 반환
 public int nextInt(int bound) //  0 이상 bound 미만 범위의 int형 난수 반환
 public float nextFloat() // 0.0 이상 1.0 미만의 float형 난수 반환
 public double nextDouble() // 0.0 이상 1.0 미만의 double형 난수 반환
```

```java
public static void main(String[] args) { // 실행할 때마다 다른 결과를 보여준다.
 Random rand = new Random(); // 씨드 값을 안넣어주면 알아서 시간값으로 받아오므로
 for(int i = 0; i < 7; i++)
 System.out.println(rand.nextInt(1000));
}
```
```java
public static void main(String[] args) { // 실행할 때마다 같은 결과를 보인다
 Random rand = new Random(12); // 씨드값이 넣어져 있으므로 
 for(int i = 0; i < 7; i++)
 System.out.println(rand.nextInt(1000));
}
```


