## Canvas
> 도형, 이미지 등의 그래프 표현을 위한 요소 

```html
var canvas = doucment.getElementById('canvas')
    context = canvas.getContext('2d') // 2차원: 평면 도형, 텍스트, 이미지 

context.font = '38pt Arial';
context.fillStyle = 'cornflowerblue';
context.strokeStyle = 'blue';

context.fillText('Hello Canvas', canvas.width/2 -150, canvas.height/2+15); // Text 내부 색상 채워줌
context.strokeText('Hello Canvas', canvas.width/2 -150, canvas.height/2+15); // Text 외곽선
```

## Context 
> 실제 그리기 기능을 담당하는 객체
> Canvas는 Context를 담은 상자

- Context 속성: 색상, 스타일, 그림자, 선스타일, 텍스트, 이미지 데이터, 합성 등 

### Canvas 크기 vs Surface 크기
- Canvas 크기: 캔버스 요소가 웹페이지에서 차지하는 영역의 크기 -> **화면**
- Surface 크기: 캔버스에 그려질 이미지 데이터 저장 영역의 크기 -> **메모리**
- HTML에서 크기 지정할 경우 두 크기는 동일
- **CSS에서 Canvas 크기 속성 지정할 경우, 두 크기가 다를 수 있음.**

## 도형 그리기
- 좌표계: y축이 반대 방향으로 돼있다. 
- 사각형
  - clearRect(double x, double y, double w, double h): 사각형 영역에 해당되는 사각형을 지우는 함수
  - strokeRect(double x, double y, double w, double h): 사각형 영역의 외곽선 그리는 함수
  - fillRect(double x, double y, double w, double h): 사각형 영역을 채우는 함수
       
