## currying-function

> 리덕스 미들웨어를 직접 만들어보는 예제를 공부하던 도중, 사용해보지 않았던 문법을 만나게 되어 정리한다.

```jsx
const middleware = (store) => (next) => (action) => {
  // 하고 싶은 작업...
};
```

- 위 함수는 curry function으로 next에 쌓이는 미들웨어를 실행하고 마지막엔 dispatch로 action을 실행시켜주는 리덕스 예시 코드이다.

### 왜 사용하는가?

- 커링을 통해 함수의 부수효과를 줄일 수 있다.
- 가독성과 유지보수를 용이하게 하기 위해 사용한다.

### 어떻게 사용하는가?

- 커리 함수는 함수를 매개 변수로 받는다.
- 실행 시점에 매개 변수로 받은 함수의 인자를 사용하는 함수를 다시 반환한다.
- 반환된 함수는 클로저에 의해 전달된 함수를 기억한다.

- 간단한 두 수의 합을 구하는 함수가 있다고 가정한다.

```jsx
function sum(a, b) {
  return a + b;
}
```

- 이를 curry-function으로 바꾸게 되면 아래와 같이 구현한다.

```jsx
function currying(func) {
  return function (a) {
    return function (b) {
      return func(a, b);
    };
  };
}
```

- currying 함수가 실행되는 시점에 아래와 같은 함수가 return 된다.
  - 이때 매개변수 func가 클로저가 된다.

```jsx
function(a) {
    return function(b) {
      return func(a, b);
    }
  }
```

- 그 후 다시 함수는 호출 시점에 아래와 같은 함수를 return 한다.
  - 이때 func, a는 클로저가 되어 기억하고 있다.

```jsx
function(b) {
      return func(a, b);
    }
```

- 마지막 매개 변수인 b를 받아 호출하는 시점에 기억하고 있던 func, a, b를 사용해 결과를 return한다.

```jsx
const curry = currying(sum)(10)(20);
// 30
```

- 이는 화살표 함수로 변환할 수 있다.

```jsx
const currying = (func) => (a) => (b) => func(a, b);
```
