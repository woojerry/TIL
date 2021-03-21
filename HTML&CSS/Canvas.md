## Canvas
> 도형, 이미지 등의 그래프 표현을 위한 요소 

```jsx
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

#### Canvas 크기 vs Surface 크기
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

#### 색상과 투명도    
```jsx
context.strokeStyle = 'goldenrod';
context.fillStyle = 'rgba(0, 0, 255, 0.5)'; // 0.5는 투명도
```
#### 그림자
- shadowColor: 불투명한 색상으로 지정해야 그림자가 보임.
- shadowBlur, shadowOffsetX, ShadowOffsetX : 이 중 하나의 값이 0이 아니어야 그림자가 보임.

## 경로
> 일련의 직선, 곡선으로 구성된 복잡한 도형 표현
- Stroke: 외곽선 그리기, fill: 내부 채우기
- 과정: **beginPath -> 도형 -> stroke/fill**
- 닫힌 도형: **beginPath -> 도형 -> closePath -> stroke/fill**
- 직선:  **beginPath -> moveTo -> lineTo -> stroke
    - **직선을 그릴 때 위치를 0.5를 더해줘야 원하는 위치에 나타난다.** 

#### 직선 관련 속성
- lineCap(직선의 양쪽 끝 마무리): butt(default), round, square
- lineJoin(직선들이 맞닿는 위치 표현): miter(default),bevel, round
    - miterLimit : lineJoin속성이 miter일 경우, 최대 길이를 제한. 길이가 miterLimit보다 클 경우, bevel처럼 취급

### 원호 그리기
- arc(x, y, radius, Math.PI/4, Math.PI, false)
- arc(x, y, radius: 원의 반지름, 시작각도, 끝각도, 시계/반시계 방향) 
- Math.PI = 180도, Math.PI/4 = 45도, 시계방향 = false, 반시계방향 = true

### 베지어 곡선
> **양 끝점과 2개의 제어점을 이용**한 곡선 그리기 

<hr>

## Text
### 함수
- stroke: 외곽선 그리기  
- fill: 내부 채우기
