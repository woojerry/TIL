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

<hr>

## Container 속성값
- **우선 flexbox로 만들고 싶으면 ```display: flex;```를 주면 된다.**

#### flex-direction
- flex-direction: row; (기본값)
- row-reverse(오른쪽에서 왼쪽), column(기본축 반대로), column-reverse(아래에서 위로)

#### flex-wrap
- nowrap이 기본값 -> 아이템들 한줄에 
- wrap -> 아이템들이 꽉차게 되면 다음라인으로
- wrap-reverse(반대로 wrapping)

#### justify-content
> 중심축에서 아이템들의 배치
- justify-content: flex-start; (기본값) - 왼쪽에서 오른쪽으로(수직축이 중심축이라면 즉, flex-direction이 colmin일 때 위에서 아래로)
- justify-content: flex-end; - 오른쪽축으로 item들을 배치(수직축이 중심축이라면 밑에서 위로)
- justify-content: center; - 아이템들을 가운데로
- justify-content: space-around;, space-evenly, space-between- item들에 space가 들어가 배치

#### align-itmes
- align-items: baseline; - text에 따른 baseline에 맞춰서 배치

#### align-content
> 반대축에서 아이템들의 배치
- justify-contnet와 속성 동일

<hr>

## Item 속성값
