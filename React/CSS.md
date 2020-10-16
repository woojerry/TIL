## CSS

### Boostrap
  - React ver. 설치 방법 : React Boostrap 이용
      - npm install react-bootstrap bootstrap
  - CSS link 태그```<link [내용]/>``` index.html에 복사
  
### Component 가져오기  
  - React-Bootstrap 사이트에서 원하는 Component의 코드 APP component에 붙여넣기 
  - 사용할 **Component를 import**해와야 사용 가능
  ```jsx
  // React-Component import 방법
  import Button from 'react-bootstrap/Button';

  // or less ideally
  import { Button } from 'react-bootstrap';
  ```
###   
- React에서 프로젝트 폴더 중 **public**폴더에 이미지를 보관 (발행해도 파일이 그대로 남아있음)
    - src 안에 있는 파일은 리액트 앱을 발행했을 때 압축될 수 있다.
    
- 배경 그림 넣기 
     - App.css 파일에서 특정 클래스 안에 ```background-image : url(/[이미지파일명]);```
     - public 폴더안에 있는 이미지이므로 ```/```로 경로를 나타내도 public 폴더 내부에 있는 이미지들을 갖다쓸 수 있다.
