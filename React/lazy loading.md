## lazy loading
> App.js에 import가 너무 많을 때, 메인페이지 방문시 모든 것을 import 해오면 사이트 초기 접속속도가 매우 느려질 수 있다. 그래서 그 Component가 필요할 때 import 해오도록 해주는 것

- 사용법 ex)Detail 컴포넌트로
1. ```import {lazy, Suspense} from 'react';``` import 해오기
2. ```import Detail from './Detail.js';``` -> ```let Detail = lazy(() => { return import('./Detail.js'); });```
3. ```<Suspense>```컴포넌트로 감싸주기
4. fallback 속성에는 ```원하는 컴포넌트 로딩 전까지 띄울 원하는 HTML을 적기 
```jsx
<Suspense fallback={ <div>로딩중입니다~!</div> }>
      <Detail/>
</Suspense>
```
