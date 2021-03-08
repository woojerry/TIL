## class & id
### class 
> 하나의 클래스를 여러 요소에 공통적으로 적용 가능

### id
> 하나의 id는 하나의 요소에만 적용 가능

<hr>

## HTML Tags
### p
> 문장들을 집어넣는 태그

### ul, ol, li 
> unordered list, orederd list, li는 목록안에 들어가는 항목들

### em
> 이탤릭체로 강조 

### strong
> 굵은 글씨로 강조

### span, div
> span - 작은 영역, div - 여러개의 영역

  
## 선택자
### 자손 선택자
> 다른 요소의 하위 계층에 속한 요소들을 선택 
```jsx
h1 em -> selects em elements contained in an h1
div p -> selects p elements contained in a div
```

### 클래스 선택자
> 특정 클래스로 지정된 요소들을 선택
> 둘 이상의 클래스를 함께 명시할 수 있음

```jsx
.bar .highlight -> bar와 hightlight 클래스 모두 선택
```

### 스타일의 상속
> 스타일 속성은 계층 구조에 따라 상속됨

### 스타일의 종속
> 선택자는 위에서부터 아래로 내려오면서 매치된다.
- 그 요소를 선택할 수 있는 가장 **구체적인** 선택자 중 **가장 나중에 기술된 것을 대응**시킨다.

### JS를 HTML에 연동시키는 방법
- 1. HTML문서에 직접 포함시키기 (```<body>```안 ```<scrip>```안에서)
- 2. 외부파일로 만들고 참조
