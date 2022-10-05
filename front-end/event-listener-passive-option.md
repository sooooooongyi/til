## event listender passive option

> 스크롤을 위한 이벤트 리스너 추가 중 passive라는 옵션을 발견했다!

- passive가 true인 경우, preventDefault() 함수를 절대 호출하지 않음으로써 성능을 대폭 향상 시킬 수 있는 웹 표준 기능입니다.
- 터치 기반의 모바일 디바이스에서 효과를 기대해볼 수 있다.
- 명시하지 않을 경우의 기본 값은 `false`지만, Safari와 Internet Explorer를 제외한 브라우저에서 `[wheel` (en-US)](https://developer.mozilla.org/en-US/docs/Web/API/Element/wheel_event), `[mousewheel` (en-US)](https://developer.mozilla.org/en-US/docs/Web/API/Element/mousewheel_event), `[touchstart](https://developer.mozilla.org/ko/docs/Web/API/Element/touchstart_event)`, `[touchmove` (en-US)](https://developer.mozilla.org/en-US/docs/Web/API/Element/touchmove_event) 이벤트에서의 기본 값은\* `true`
  입니다.
