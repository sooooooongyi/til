## redux

- 상태관리를 위한 라이브러리

![스크린샷 2022-03-13 오후 10 42 05](https://user-images.githubusercontent.com/69751205/158326304-f4533e1b-73cd-4b76-a538-84359842f83e.png)

- action이 발생하면 reducer를 호출하고, reducer는 store를 통해 상태를 저장한다. store가 변경되면 다시 리렌더링된다.
- 미들웨이 기능을 제공한다.
- 성능 최적화를 제공한다.
- 절차가 Context API보다 복잡하기 때문에 큰 규모의 프로젝트에 사용하는 것이 좋다.

### 1. 진실은 하나의 근원으로부터

- 하나의 저장소 안에 하나의 객체 트리 구조로 저장됩니다.

### 2. 상태는 읽기 전용이다.

- action과 reducer를 통해서만 상태를 변경할 수 있다.

### 3. 변화는 순수 함수로 작성되어야한다.

- reducer 안에는 네트워크 로직이 들어가선 안된다.
- 항상 같은 입력에 대한 같은 출력이 나와야한다.

## keywords

- Action
  - 상태에 어떠한 변화가 필요하게 될 떼 액션을 발생시키는데, 하나의 객체로 표현된다.
  - 액션 생성 함수는 액션을 만드는 함수입니다. 액션에 넣을 값을 받아와 액션 객체 형식으로 만든다.
  ```jsx
  export function addDog(data) {
    // return 값이 액션
    return {
      type: 'ADD_DOG',
      data,
    };
  }
  ```
- Reducer
  - 변화를 일으키는 함수.
  - 현재의 상태와 전달 받은 액션을 참고하여 새로운 상태를 만들어서 반환합니다. (액션에 따른 switch문 사용)
- Store
  - 한 애플리케이션당 하나의 스토어를 만들게 됩니다.
  - 현재의 앱 상태, 리듀서가 들어갑니다. (내장 함수도 있다.)
- dispatch
  - 내장함수 중 하나로 액션을 발생시킨다.
  - 파라미터에 액션을 전달하면 스토어에서 리듀서 함수를 실행시켜 액션을 처리하는 로직을 수행해 상태를 변화시킨다.
- subscribe
  - 함수 형태의 값을 파라미터로 받아옵니다.
  - 특정 함수를 전달해주면, 액션이 디스패치 되었을 때 마다 전달해준 함수가 호출됩니다.
  - react-redux에선 connect 함수 또는 useSelector Hook을 사용하여 리덕스 스토어의 상태에 구독한다.

## connect

- connect는 HOC (Higher-Order-Component)를 의미한다.
  - HOC는 컴포넌트를 인자로 받아 새로운 컴포넌트를 반환하는 함수
  - with~ 이름을 붙인다.
- 컴포넌트를 특정 함수로 감싸서 특정 값 또는 함수를 props로 받아와서 사용할 수 있게 해주는 패턴이다.

```jsx
import React, { useCallback } from 'react';
import { connect } from 'react-redux';
import Todos from '../components/Todos';
import { addTodo, toggleTodo } from '../modules/todos';

function TodosContainer({ todos, addTodo, toggleTodo }) {
  const onCreate = (text) => addTodo(text);
  const onToggle = useCallback((id) => toggleTodo(id), [toggleTodo]); // 최적화를 위해 useCallback 사용

  return <Todos todos={todos} onCreate={onCreate} onToggle={onToggle} />;
}

export default connect((state) => ({ todos: state.todos }), {
  addTodo,
  toggleTodo,
})(TodosContainer);
```

- connect에 있는 state가 props의 state로 전달되고 두번째 객체가 함수로 들어간다.

```jsx
const mapDispatchToProps = (dispatch) =>
  // bindActionCreators 를 사용하면, 자동으로 액션 생성 함수에 dispatch 가 감싸진 상태로 호출 할 수 있습니다.
  bindActionCreators(
    {
      increase,
      decrease,
      setDiff,
    },
    dispatch
  );
```

- bindActionCreators를 사용하면 액선 생성함수에 자동으로 dispatch를 감싸준다.
