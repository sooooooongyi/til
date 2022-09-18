## [window.open](http://window.open) in ios safari

- 아이폰 사파리 환경에선 window.open()이 동작하지 않은 경우가 발생한다.
- 보안 정책 때문에 발생하는 경우이고, click event에서만 window.open()을 통한 팝업이 허용되고 있다.
  - 네트워크 통신 시 동작하지 않는다.
  - 다른 스코프의 함수에선 동작하지 않는다.
  - click 이벤트를 제외하고 동작하지 않는다.

## 해결법

- 우회하는 방법

```jsx
const myWindow = window.open();
myWindow.location.href = '';
```

- 비동기 시 처리 방법

```jsx
function API() {
  let myWindow = window.open();

  $.ajax({
    url: '/userAction.do',
    type: 'GET',
    success: function (data) {
      myWindow.location = data.url;
    },
  });
}
```
