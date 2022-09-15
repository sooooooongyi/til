## BEM 방식

- BEM은 Block, Element, Modifier를 의미
- 저 세가지로 구성된 CSS 클래스 이름을 명명하는 방법
- 각각 요소는 `—` 또는 `__` 로 구분합니다.
- 어떻게 보이는가가 아닌, 어떤 목적인가?에 따라 이름을 짓습니다.

### Block

- UI의 한 덩어리를 표현하는 부분
- 재사용 가능한 기능적으로 독립적인 페이지 컴포넌트

### Element

- 블록을 구성하는 단위
- 독립적이지 않고, 의존적인 형태
- 자신이 속한 블럭 내에서만 의미를 가진다.
- 중첩이 가능하지만 하위 요소를 표현하기 위해 가장 가까운 상위 요소를 채택하지 않는다.

```jsx
<form class="search-form">
  <div class="search-form__content">
    <input class="search-form__input" />
    <button class="search-form__button">Search</button>
  </div>
</form>
```

### Modifier

- 블록이나 엘리먼트의 속성을 담당
- 생긴게 조금 다르거나, 다르게 동작하는 블럭 또는 엘리먼트를 만들 때 사용

```jsx
// --focused는 true라고 가정하고 사용함 -> 불리언 타입

<ul class="tab">
  <li class="tab__item tab__item--focused">탭 01</li>
  <li class="tab__item">탭 02</li>
  <li class="tab__item">탭 03</li>
</ul>
```

```jsx
// --color-grays는 key-value 타입으로 하이픈을 사용

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

### 장점

- 클래스 네임으로 마크업 구조를 알 수 있다.
- SASS와 함께 사용하기 좋다.
  - 자식 클래스를 &\_\_logo 로 작성하기 때문에 쉽게 찾을 수 있다.
  - nesting을 깊게 작성하지 않아도 된다.

```jsx
.header {
   .nav {
      position: absolute;
      .list {
         list-style: none;
      }
      .item {
         outline: 0;
         .link {
            color: red;
         }
      }
   }
}

.header {
   &__nav {
      position: absolute;
   }
   &__list {
      clor: red;
   }
   &__item {
      outline: 0;
   }
   &__link {
      color: red;
   }
}
```

### 단점

- 클래스 네임이 길다.
