## **orientationchange**

> 장치의 방향이 바뀔 때 호출되는 이벤트

### 사용예시

```jsx
// Note that "orientationchange" and screen.orientation are unprefixed in the following
// code although this API is still vendor-prefixed browsers implementing it.
screen.addEventListener('orientationchange', function () {
  alert('the orientation of the device is now ' + screen.orientation);
});
```
