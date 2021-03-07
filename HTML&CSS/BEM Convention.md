### BEM Convention(BEM 방식)
> CSS 클래스네임을 어떻게 지으면 좋은지에 대한 CSS방법론 중 하나.

- 개발, 디버깅, 유지보수를 위하여 CSS 선택자의 이름을 가능한 한 명확하게 만드는 것이 목표.
- **소문자, 숫자 만을 이용해서 작명**

```jsx
.header__navigation--navi-text {
  color: red;
}
```
- 위 코드에서 ```header```는 **Block**, ```naviagtion```은 **Element**, ```navi-text```는 **Modifier**
- BEM은 Block, Element, Modifier를 뜻한다.
- BEM은 기본적으로 **ID를 사용하지 않으며, class만을 사용**한다.
- '어떻게 보이는가'가 아니라 **'어떤 목적인가'**에 따라 이름을 짓는다.
- 이름을 연결할 때는 ```block-name```과 같이 하이픈 하나만 써서 연결한다.

#### Block 
> 재사용 가능한 기능적으로 독립적인 페이지 컴포넌트
- **블록은 환경에 영향을 받지 않아야 한다. 즉, 여백이나 위치를 설정하면 안된다.**
- 블록은 서로 중첩해서 작성 할 수 있다.
    - ```.header>.logo```는 header 블럭 안에 logo 블럭이 들어간 형태

#### Element
> 블록안에서 특정 기능을 담당하는 부분. 블럭은 독립적인 형태인 반면, 엘리먼트는 **의존적인** 형태이다.
- 자신이 속한 블럭 내에서만 의미를 가지기 때문에 블럭 안에서 떼어다 다른 데 쓸 수 없습니다.

```jsx
<form class="search-form">
    <input class="search-form__input"/>
    <button class="search-form__button">Search</button>
</form>
```
- 위 예시에서 ```.search-form```은 블럭이고, ```.search-form__input```과 ```.search-form__button```은 엘리먼트. search-form이란 블럭은 떼어내서 요기조기 마음껏 붙여도 됩니다. 하지만 내부의 input과 button은 검색을 위한 인풋창이자 버튼이기 때문에, search-form 안에서만 존재 의미가 있는 엘리먼트입니다.

- 엘리먼트 또한 중첩이 가능. 특징으로는 예를들어 ```.block > .block__element1 > .block__element2``` 구조에서 ```.block_element2```를 ```.block_element1```의 하위 엘리먼트로 보지 않고 둘 다 똑같이 ```.block```의 엘리먼트로 취급한다.
- 따라서 **클래스네임에 캐스케이딩을 여러번 표시할 필요가 없다.**
- 
```jsx
// BEM에서는 이렇게 사용하지 않는다
<form class="search-form">
  <div class="search-form__content">
      <input class="search-form__content__input"/>
      <button class="search-form__content__button">Search</button>
  </div>
</form>
```
```jsx
// 올바른 예
<form class="search-form">
  <div class="search-form__content">
      <input class="search-form__input"/>
      <button class="search-form__button">Search</button>
  </div>
</form>
```

#### Modifier
> 블럭이나 엘리먼트의 속성을 정의. 불리언(boolean) 타입과 키-밸류(key-value) 타입이 있다.

```jsx
<ul class="tab">
  <li class="tab__item tab__item--focused">탭 01</li>
  <li class="tab__item">탭 02</li>
  <li class="tab__item">탭 03</li>
</ul>
```
- 위 예제는 boolean타입으로 수식어가 있으면 값이 true 라고 가정한다. (```--focused```가 수식어)

```jsx
<div class="column">
  <strong class="title">일반 로그인</strong>
  <form class="form-login form-login--theme-normal">
    <input type="text" class="form-login__id"/>
    <input type="password" class="form-login__password"/>
  </form>
</div>
 
<div class="column">
  <strong class="title title--color-gray">VIP 로그인 (준비중)</strong>
  <form class="form-login form-login--theme-special form-login--disabled">
      <input type="text" class="form-login__id"/>
      <input type="password" class="form-login__password"/>
  </form>
</div>
```
- key-value 타입은 ```-```로 연결해 표시한다. 여기서는 ```color-gray```과 ```theme-normal```
