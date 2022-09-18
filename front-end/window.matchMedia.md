## window.matchMedia

- 자바스크립트에서 CSS의 미디어쿼리를 이용할 때 사용하는 함수

```jsx
var media = window.matchMedia(mediaQueryString);

// 여기서 mediaQueryString은 CSS 미디어쿼리 문법이 들어간다.
```

- matchMedia() 함수는 MediaQueryList를 반환하는데 `media` 와 `matches` 라는 두 프로퍼티가 존재한다.
  - `media` 는 사용한 미디어쿼리 문자열을 반환한다.
  - `matches` 는 현재 화면에 미디어쿼리의 범위에 들어가면 `true`, 아니면`false` 를 반환한다.

```jsx
var m = matchMedia("screen and (min-width: 768px)");
m.media; // "screen and (min-width: 768px)"
m.matches; // false
```
