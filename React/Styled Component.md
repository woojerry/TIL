## Styled Component
> component가 많아졌을 때, 

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
