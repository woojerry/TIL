## 배열
  - 배열 생성
  ```int[] arr = new int[3];```
  
  - 배열 생성 및 초기화 
  ```int[] arr = {1,2,3};```
  
  - 배열의 디폴트 초기화
    - 기본 자료형 배열의 모든 요소 0으로 초기화
    - 인스턴스 배열(참조변수 배열)은 모든 요소 null로 초기화
  
  - 1차원 배열
  - ```int[] ref;``` int형 변수로 이루어진 배열을 참조하는 참조변수 생성    
  ```ref= new int[5];``` 인스턴스 생성
  
  - 인스턴스 대상 1차원 배열의 예
  ```
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
  
  
