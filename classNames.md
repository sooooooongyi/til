## classNames

- CSS 클래스를 조건부로 설정 할 때 매우 유용한 라이브러리입니다.

### 사용법

```jsx
import classNames from 'classnames';

classNames('one', 'two'); // 'one two'
classNames('one', { two: true }); // 'one two'
classNames('one', { two: false }); // 'one'
classNames('one', ['two', 'three']); // 'one two three'

const myClass = 'hello';
classNames('one', myClass, { myCondition: true }); //'one hello myCondition'
```

- true, false 값을 줘서 클래스를 넣을 건지 안넣을 건지 분기할 수 있다.

```jsx
const MyComponent = ({ highlighted, theme }) => {
  <div className={classNames('MyComponent', { highlighted }, theme)}>
    Hello
  </div>;
};
```

- classNames 사용 없이 조건부나 삼항 연산자를 사용하게 되면 가독성이 떨어진다.

```jsx
const MyComponent = ({ highlighted, theme }) => {
  <div className={`MyComponent ${theme} ${highlighted ? 'highlighted' : ''}`}>
    Hello
  </div>;
};
```

- classNames를 불러올때 `classnames/bind`를 미리 styles에서 받아와 사용할 수 있게끔 설정한다.
- 그 후 `cx(’class1’, {class2 : true})` 이런식으로 사용한다.

```jsx
import classNames from 'classNames/bind';

const cx = classNames.bind(styles);
```
