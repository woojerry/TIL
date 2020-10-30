## Styled Component
> Component가 많아져 헷갈릴 때 스타일을 바로 입혀 Component를 만드는 방식

- 우선 터미널에서 ```yarn add styled-components``` 또는 ```npm install styled-components```
- ```import styled from 'styled-compnents';```로 import 해오기 
- className 작명 없이 컴포턴트에 직접 스타일을 넣어 스타일링함. CSS를 미리 입히는 것.
- let [Component이름] = styled.[원하는태그]`[원하는CSS]`; (백틱 안에 원하는 CSS 넣기)
```jsx
let Box = styled.div` // CSS를 미리 입혀놓은 box 컴포넌트
  padding : 20px; // padding 20px이 입혀짐.
`;
let Title = styled.h4`
    font-size : 25px;  
`;
```
```jsx
retrun(
<Box>
   <Title>Detail</Title>
        </Box>
)
```

- 비슷한 UI가 여러개 필요할 경우 -> props 사용해 스타일링
- React애서 prpos 전송할 때
    - 일반 텍스트를 전달하고 싶으면 "" 따옴표 안에 쓰고, 변수나 자료형을 담고 싶으면 {} 중괄호 안에 씀
```jsx
let Title = styled.h4`
    font-size : 25px;  
    color : ${ props => propss.색상} // 백틱안에 ${} 문법 사용
`;

retrun(
<Box>
   <Title 색상 ="blue">Hello</Title>
   <Title 색상 ={'red'}>Hello</Title>
        </Box>
)
```

## SASS
> CSS를 프로그래밍언어처럼 작성가능한 Preprocessor

- 터미널에서 ```yarn add node-sass``` 또는 ```npm install node-sass```로 설치
- 브라우저는 SASS문법을 모르므로 다시 CSS로 컴파일 해야한다.(nodes-sass이 자동으로 해주는 역할)
- .css 파일이 아닌 .scss파일로 만들어준다.
- SASS문법 사용이유
    1. 변수 사용 : 변수를 만들어 원하는 곳에서 사용, 특정 px값 %값 쉽게 사용
    ```jsx
      $mainColor : #ff0000;
      
      .red{
        color : %mainColor;
      }
    ```
    2. @import : CSS 중 자주 사용하는 스타일을 저장해두고 import해올 때 사용
    ``` 
    @import './reset.scss'; // reset.scss파일 import
    ``` 
    3. nesting : CSS selector가 너무 길고 복잡할 때 대신 사용. selector해석이 쉽고 관련 class끼리 관리 용이
    ```jsx
        div.container h4 {
          color : blue;
        }
        div.container p {
          color : green;
        }
    ```
    ```
    div.container {
        h4 {
          color : blue;
        }
        p {
          color : green;
        }
    }    
    ```   
    
    4. extend : SASS문법에서의 복붙 
    ```jsx
    .my-alert {
      background : #eeeeee;
      padding : 15px;
      border-radius : 5px;
      max-width : 500px;
      width : 100%;
      margin : auto;
    }
    .my-alert2 {
      @extend .my-alert;
      background : yellow;
    }
    ```
    5. @mixin/ @include : SASS에서의 함수
    ```jsx
    @mixin function() { // mixin이 function 키워드
      background : #eeeeee;
      padding : 15px;
      border-radius : 5px;
      max-width : 500px;
      width : 100%;
      margin : auto;
    }
    .my-alert {
      @include function() // @include로 함수 불러오기
    }
    ```
