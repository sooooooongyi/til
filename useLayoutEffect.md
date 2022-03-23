## useLayoutEffect

- react에서 제공하는 life cycle hook중 하나로 레이아웃의 배치와 그리기를 완료한 후 발생하는 useEffect와 다르게 DOM이 화면에 그려지기 전에 호출되는 hook이다.
- 아래 다이어그램을 보면 effect보다 먼저 실행되는 것을 알 수 있다.

![스크린샷 2022-03-23 오후 11.51.09.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6249721d-8e8b-4f88-9a5b-d2578d864529/스크린샷_2022-03-23_오후_11.51.09.png)

### 사용법

- useEffect와 동일하다.

```jsx
useLayoutEffect(() => {
  // effect
  return () => {
    cleanup;
  };
}, []);
```
