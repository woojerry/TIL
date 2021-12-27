## querySelector vs querySelectorAll
### querySelector
> 특정 name,id,class를 제한하지 않고 css선택자를 사용하여 요소를 찾는다.
- **같은** id 또는 class 일 경우 스크립트의 **최상단 요소만 로직에 포함**
```js
const secondHand = document.querySelector('.second-hand');
```

### querySelectorAll
> 선택자를 선택하여 배열과 비슷한 객체인 nodeList를 반환합니다.
- 반환객체가 nodeList이기에 ```for```문 또는 ```forEach```문을 사용
```js
const inputs = document.querySelectorAll('.controls input');
inputs.forEach(input => input.addEventListener('change', handleUpdate)); // input값 바뀌면 handleUpdate 함수 호출
```
