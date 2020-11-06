## Tab
- React-bootstrap에서 Base-Nav에서 Tabs 복사해 사용
- ```import {Nav} from 'react-bootstrap';```

## Animation 추가
- 터미널에서 ```npm install react-transition-group``` 또는 ```yarn add react-transition-group```로 라이브러리 설치4
- import {CSSTransition} from "react-transition-group";로 import해오기
```
1. <CSSTransition>으로 애니메이션 필요한 곳 감싸기
2. in, classNames, timeout 넣기
3. class로 애니메이션 넣기
4. 원할 때 스위치 켜기
```
