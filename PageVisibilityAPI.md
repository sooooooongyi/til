## **Page Visibility API**

- Page Visibility API는 웹페이지가 visible 또는 focus 상태인지 알려준다.
- 사용자가 웹페이지를 최소화하거나 다른 탭으로 이동했을 때, 이 API는 페이지의 visibility를 관찰하는 visibilitychange 이벤트를 전달한다.

### document.hidden, document.visibilityState

- hidden → 보이지 않을 때 true, 보일 때 false
- visibilityState
  - visible → 윈도우의 맨 앞쪽 탭임을 의미
  - hidden → 사용자에게 보이지 않는다. 뒤쪽 탭이거나, OS Screen이 Lock
    (목적이 있게 숨겨진 것으로 간주한다.)
  - prerender → 페이지 컨텐츠가 프리렌더 되고 있으며 유저에게 보이지 않는다.
  - unloaded → 페이지가 메모리부터 unload 되고 있다.

### **visibilitychange 이벤트**

- 브라우저 탭의 컨텐츠가 visible 또는 hidden 상태로 변화할 때 발생된다.
- bubbling OK! cancle NO!

### 사용법

```jsx
document.addEventListener('visibilitychange', function () {
  console.log(document.visibilityState);
});
```

### reference

- [https://developer.mozilla.org/ko/docs/Web/API/Page_Visibility_API](https://developer.mozilla.org/ko/docs/Web/API/Page_Visibility_API)
