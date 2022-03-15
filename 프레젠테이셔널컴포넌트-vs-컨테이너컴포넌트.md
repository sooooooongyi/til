## 프리젠테이셔널 컴포넌트 vs 컨테이너 컴포넌트

### 프리젠테이셔널 컴포넌트

- 오직 뷰만 담당하는 컴포넌트
- DOM 요소와 스타일을 가지고 있다.
- 오직 props으로만 데이터를 가져오고, 화면에 보여주는 역할을 한다.
- 대부분 state가 없으며, 있다면 UI를 위한 state를 가진다.

```jsx
import React from 'react';

function Counter({ number, onIncrease, onDecrease }) {
  return (
    <div>
      <h1>{number}</h1>
      <button onClick={onIncrease}>+1</button>
      <button onClick={onDecrease}>-1</button>
    </div>
  );
}

export default Counter;
```

### 컨테이너 컴포넌트

- 데이터 핸들링에 대한 역할을 한다.
- DOM 요소와 스타일 요소가 없으며, 있다면 감싸는 용도로 사용된다.
- 리덕스의 액션, 상태 변경에 대한 로직을 담고 있고 프레젠테이셔널 컴포넌트에 데이터를 전달하거나 함수를 제공한다.
- 다른 프레젠테이셔널 컴포넌트나 컨테이너 컴포넌트를 관리한다.

```jsx
import React from 'react';
import Counter from '../components/Counter';
import { useSelector, useDispatch } from 'react-redux';
import { increase, decrease } from '../modules/counter';

function CounterContainer() {
  const number = useSelector((state) => state.counter);
  const dispatch = useDispatch();

  const onIncrease = () => {
    dispatch(increase());
  };
  const onDecrease = () => {
    dispatch(decrease());
  };

  return (
    <Counter number={number} onIncrease={onIncrease} onDecrease={onDecrease} />
  );
}

export default CounterContainer;
```

### 왜 하는거죠?

- MVC, MVVM 패턴처럼 기능에 따라 분리하기 위해 사용된다.
- 프리젠테이셔널 컴포넌트는 UI적 요소, 즉 View를 담당한다.
- 컨테이너 컴포넌트는 Data와 로직을 담당한다.
- 이를 분리함으로 재사용성과 가독성을 높이고, 개발을 편리하게 할 수 있다.
