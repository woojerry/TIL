## Input
  - React에서는 HTML과 달리 <input>태그를 꼭 닫아줘야함 ```<input/>``` 
  - input Eventhandler -  onChange(), onInput()
    - React에서는 onChange와 onInput이 무언가를 입력 받았을 때 실행하도록 하는 것으로 같다.
    - 사용자가 입력한 값을 가져오는 것 ```e.target.value ```
    ```jsx
    <input onChange={ (e)=> { e.target.value } } />
    ```
