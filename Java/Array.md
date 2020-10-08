## 배열
  - 배열 생성
  ```int[] arr = new int[3];```
  
  - 배열 생성 및 초기화 
  ```int[] arr = {1,2,3};```
  
  - 배열의 디폴트 초기화
    - 기본 자료형 배열의 모든 요소 0으로 초기화
    - 인스턴스 배열(참조변수 배열)은 모든 요소 null로 초기화
  
  ### 1차원 배열
  - ```int[] ref;``` int형 변수로 이루어진 배열을 참조하는 참조변수 생성    
  - ```ref= new int[5];``` 인스턴스 생성
  
  - 인스턴스 대상 1차원 배열의 예
    ```java
    class Box{
      priavte String conts;

      Box(String cont) { this.conts = cont;}
      public String toString(){
        return conts;
      }
    }
    class ArrayIsInstance2 {
      public static void main(String[] args){
        Box[] ar = new Box[5]; // 길이가 5인 Box형 1차원 배열의 생성
      }
    }
  
  ### for-each문
  ```java
      int [] ar = {1,2,3,4,5};
      for(int e : ar) { // 배열 안에 있는 값 돌릴 때
        System.out.println(e);
      }
  ```
    
  ```java
        Box[] ar = new Box[5];
        for(int e : ar){
          System.println(e);
        }
  ```

  ### 2차원 배열
  - ```int[][] arr = new int[3][4];``` 2차원 배열 생성
  - ```int[][] arr = {11},{22,33},{44,55,66}``` 이렇게 만들면 가변배열 
  ```java
  public static void main(String[] args) {
    int[][] arr = {
      {11},
      {22, 33},
      {44, 55, 66}
    };
    
    for(int i=0; i < arr.length; i++) {
      for(int j =0; j < arr[i].length; j++) {
        System.out.print(arr[i][j] + "\t");
      }
      System.out.println();
    }  
  }
  ```
  
  
  
  
