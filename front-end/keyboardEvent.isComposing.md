## keyboardEvent.isComposing

> textarea를 조작하는 도중, 키보드 이벤트에 대해 이벤트가 두번 핸들링되는 현상이 발생했다.

- 해당 현상은 크롬 브라우저에서 textarea에 한글을 사용하는 경우 발생한다.
- 한글의 경우 자음과 모음의 조합으로 한 음절이 만들어지는 조합 문자이기 때문에 글자가 조합 중인지, 조합이 끝난 상태인지 알 수 없어 발생한다.
- isComposing이라는 프로퍼티를 사용해 조작할 수 있다.
  - 입력하고 있는 문자가 조합 문자인지, 아닌지를 boolean값으로 반환한다.

### 리액트에서 사용하기

- 리액트의 이벤트는 합성 이벤트이기 때문에 isComposing 속성이 없다.
- 사용하기 위해선 nativeEvent 어트리뷰트를 참고해야한다.

```tsx
const handleKeyDown = (event: React.KeyboardEvent) => {
  if (event.nativeEvent.isComposing) return
}
```
