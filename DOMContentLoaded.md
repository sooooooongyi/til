## DOMContentLoaded

> 초기 HTML 문서를 완전히 불러오고 분석했을 때 발생 (스타일 시트, 이미지, 하위 프레임의 로딩은 기다리지 않습니다.)

- DOM 트리를 완성하는 즉시 발생

```jsx
window.addEventListener('DOMContentLoaded', (event) => {
  console.log('DOM fully loaded and parsed');
});
```

### 비슷한 이벤트

- load - DOM 트리 + 스타일 시트, 이미지 등 외부 자원들도 모두 불러왔을 때 발생
- beforeunload, unload - 사용자가 페이지를 떠날 때 발생
