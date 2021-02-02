## FlexBox
- Flexbox는 Box에 지정되는 속성값들과 item에 들어가는 속성값들이 따로있다.
- Flexbox에는 **중심축**이 **반대축**이 있는데, 중심축이 수직인지 수평인지에 따라 반대축이 바뀐다.

### container에 지정되는 속성 값들
- display
- flex-direction
- flex-wrap
- flex-flow
- justify-content
- align-items
- align-content

### item에 지정되는 속성값들
- order
- flex-grow
- flex-shrink
- flex
- align-self

## Container 속성값
- 우선 flexbox로 만들고 싶으면 ```display: flex;```를 주면 된다.

#### flex-direction
- flex-direction: row; (기본값)
- row-reverse(오른쪽에서 왼쪽), column(기본축 반대로), column-reverse(아래에서 위로)

#### flex-wrap
- 
