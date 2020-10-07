## Event

### onClick 

```onClick ={ function() } ``` 

``` onClick = { ()=>{실행할 내용} }```

### Input
  - React에서는 HTML과 달리 <input>태그를 꼭 닫아줘야함 ```<input/>``` 
  - input Eventhandler -  onChange(), onInput()
    - React에서는 onChange와 onInput이 무언가를 입력 받았을 때 실행하도록 하는 것으로 같다.
    - 사용자가 입력한 값을 가져오는 것 ```e.target.value ```
    ```jsx
    <input onChange={ (e)=> { e.target.value } } />
    ```
    ```jsx
    <div className="publish">
          <input onChange= {(e)=>{입력값변경(e.target.value)}} />
          <button onClick={()=> {
            var arrayCopy = [...title]; // deep copy 사용
            arrayCopy.unshift(입력값); // unshift() 배열의 맨앞에 추가, push() 맨뒤에 추가.
            changeTitle(arrayCopy);
          }}>저장</button>
       </div>
