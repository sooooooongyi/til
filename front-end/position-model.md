## Position Model (Absolute, Fixed)

### Caret Position

### Offset (READ ONLY)

- 추상적인 위치가 geometry 계산이 다 끝나서, fixed number 체계로 변환되었을 때 그 때의 숫자!
- 브라우저는 계산을 효율적으로 하기위해 geometry를 한번에 계산하고 싶어한다.
- 새롭게 계산을 다시 하는 주기를 `프레임`이라고 부른다. 하지만 offset를 요청하면 그런거 상관없이 재계산을 해야한다.
- `계산을 하려면 뭐부터해야하나~` → 기준점을 잡는다. (offset parent)

### Offset Parent

(1) null → 크롬을 기준으로 그린다. 브라우저의 바운드 박스!

- root, html, body
- position: fixed
- out of dom tree (createElement 했지만 아직 append 하지 않은 애들)

(2) recursive search

- parent === position: fixed? = null
- parent === position: !static? = ok
- body: ok
- td, th, table = ok → 근데 사실 안됨... 안에 position: relative 넣어야한다.
- parent, parent continue → 계속 쭉쭉쭉 타고 올라간다. (ok = 부모안된다!)

→ `position: absolute, position: relative 인 경우가 기준점이 된다!`

```html
// 이럴때 사용해요!! static으로 쭉쭉 흘러가다가 특정한 요소가 position:
absolute일때 그 때 전체 container가 기준점 position: relative가 된다!
```

### Offset Value

- offsetLeft
- offsetTop
- offsetWidth
- offsetHeight

---

- offsetScrollTop
- offsetScrollLeft
- offsetScrollWidth
  - 진짜 컨텐츠의 width
- offsetScrollHeight
  - 진짜 컨텐츠의 height
- 변경하기 위해선 ScrollTo 메서드를 사용해야한다.

### Position: Absolute

- 기본값은 DOM상의 부모 위치 (static 위치와 똑같은 기본값을 갖는다.)
- `offset parent으로부터의 거리`

### Position: Relative

- geometry 상 width, height이 기준이 된다.
- `normal flow로 그려졌을 때의 차이값`
