## redux-saga

- 액션을 모니터링하고 있다가, 특정 액션이 발생하면 이에 따라 특정 작업을 하는 방식으로 사용합니다.
  - 비동기 작업 시 기존 요청을 취소 처리할 수 있다.
  - 특정 액션이 발생했을 때 이에 따라 다른 액션이 디스패치되게끔 하거나, 자바스크립트 코드를 실행할 수 있다.
  - 웹 소켓의 경우 Channel을 통해 더 효율적으로 코드를 관리할 수 있다.
  - API 요청이 실패했을 때 재요청하는 작업을 할 수 있다.
- generator 문법을 사용한다.

### generator

- 제네레이터 함수는 제네레이터를 반환한다.
- next()를 호출해 코드를 실행하며, yield 값을 반환하고 흐름을 멈춥니다.
  - next() 호출 시 인자를 전달할 수 있다.
- 액션을 모니터링 할 수 있다.

  ```jsx
  function* watchGenerator() {
    console.log('모니터링 시작!');
    while (true) {
      const action = yield;
      if (action.type === 'HELLO') {
        console.log('안녕하세요?');
      }
      if (action.type === 'BYE') {
        console.log('안녕히가세요.');
      }
    }
  }

  const watch = watchGenerator();
  watch.next();
  watch.next({ type: 'HELLO' });
  ```

### 설치

```jsx
yarn add redux-saga
```

### 사용법

- Ducks 패턴을 사용한다고 가정했을 때, 파일안에 saga 함수를 만든다.
  - saga 함수는 리듀서가 할 수 없는 네트워크, 콜백 등의 행위를 하고 액션을 dispatch한다.
- saga 함수들을 모니터링하는 counterSaga 함수를 만든다.

```jsx
function* increaseSaga() {
  yield delay(1000);
  yield put(increase());
}
function* decreaseSaga() {
  yield delay(1000);
  yield put(decrease());
}

export function* counterSaga() {
  yield takeEvery(INCREASE_ASYNC, increaseSaga);
  yield takeLatest(DECREASE_ASYNC, decreaseSaga);
}
```

- saga 함수들을 동시에 실행시키기 위해 rootSaga 함수를 만든다.

```jsx
export function* rootSaga() {
  yield all([counterSaga()]); // all 은 배열 안의 여러 사가를 동시에 실행시켜줍니다.
}
```

- index.js에서 미들웨어에 saga를 등록하고 rootSaga를 실행시킨다.

```jsx
const store = createStore(
  rootReducer,
  composeWithDevTools(
    applyMiddleware(
      ReduxThunk.withExtraArgument({ history: customHistory }),
      sagaMiddleware, // 미들웨어 적용
      logger
    )
  )
);

sagaMiddleware.run(rootSaga); // 실행
```

### utils

- fork
  - 매개 변수로 전달된 함수를 비동기적으로 실행한다.
- take
  - 매개 변수로 전달된 액션이 올때까지 블락된 상태로 기다린다.
- call
  - 매개 변수로 전달된 함수를 동기적으로 실행한다.
  - Promise를 리턴한다면 resolved 될때까지 call 부분에서 실행이 멈춘다.
- put
  - 리듀서에게 액션을 디스패치 한다.
- select
  - state에서 데이터를 꺼내오기 위한 함수
- delay
  - 실행중이던 함수를 잠깐 멈춥니다.
- call
  - 비동기적인 처리를 할 때 사용하며, 특정함수를 호출하고 결과물이 반환될 때 까지 기다립니다.
- takeEvery
  - 특정 액션 타입에 대해서 디스패치되는 모든 액션들을 처리하는 것
- takeLatest
  - 특정 액션 타입에 대하여 디스패치된 가장 마지막 액션만을 처리하는 함수
- 등등 많다.
