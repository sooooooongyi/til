- tabindex 전역 특성은 요소가 포커스 가능함을 나타내며, 주로 tab 키를 사용하는 연속적인 키보드 탐색에서 어느 순서에 위치할지 지정합니다.

```jsx
<p>Click anywhere in this pane, then try tabbing through the elements.</p>
<label>First in tab order:<input type="text"></label>
<div tabindex="0">Tabbable due to tabindex.</div>
<div>Not tabbable: no tabindex.</div>
<label>Third in tab order:<input type="text"></label>
```

- input과 div이 tab으로 접근이 가능하다.
- 음수 정숫값은 연속 키보드 탐색으로 접근할 수는 없지만, 자바스크립트 또는 마우스 클릭으로 포커스 가능함을 의미
  - 자바스크립트를 사용한 위젯의 접근성 확보를 위해 사용
- 대화형 콘텐츠는 0이 기본값이고, 비 대화형 콘텐츠는 -1이 기본값입니다.
- tabindex 양의 정숫값은 순서를 지정하지만, 접근성 보조기술 사용자의 페이지 탐색과 조작에 방해가 될 수 있기 때문에 문서의 요소 순서를 논리적인 순서로 배치하는것이 더 좋다.
- 최대값은 32767

### 접근성 고려사항

- 비대화형 콘텐츠에 tabindex를 추가하는것을 지양
  - 비대화형 요소를 사용해 만든 대화형 컴포넌트는 접근성 트리에 나타나지 않으므로, 보조 기술이 해당 컴포넌트로 탐색하거나 조작하는 것을 방지합니다.
