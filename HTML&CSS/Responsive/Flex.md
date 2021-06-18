# Flex

- ```<body>```를 제외하고 모든 것은 부모이자 자식 요소가 될 수 있다.
## 부모요소에 쓰는 속성
- display:flex / justify-content / align-items/ flex-direction / flex-wrap / align-content

## 자식요소에 쓰는 속성
- flex / order / align-self / 자식요소 사용하는 margin 속성

## inline-flex 
> 자식요소의 내용만큼 너비가 줄어드는 것 

### justify-content
> 자식요소들의 좌측, 중앙, 우측 등 **수평배치**
- center / flex-start / flex-end
- space-around: 여러 개의 자식 요소끼리 좌우 간격을 일정하게 배분해서 수평 중앙에 정렬
- space-between: 여러 개의 자식 요소를 부모요소의 좌우 여백 없이 꽉 채우면서 중앙에 배치   

### align-items
> 자식요소들의 상단, 중앙, 하단 등 **수직배치**
- center / flex-start / flex-end

### flex-direction
> 자식요소의 가로배치 세로배치, 정방향 배치, 역방향 배치
- row (default) / row-reverse / column / colunmn-reverse
- **모바일 버전일 때, flex-direction을 row에서 column으로 바꿀 때 있다.**

### flex-wrap
> 부모요소의 너비값 안에서 줄바꿈 없이 배치할지 줄을 바꿀지 결정
- nowrap: 자식요소의 줄 안바꾸고 너비 강제로 줄이기
- wrap: 자식 요소의 너비를 줄이지 않으면서 줄을 바꿈
- wrap-reverse: 
