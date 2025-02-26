## 리액트의 render phase와 commit phase에 대해서 설명해주세요.

### render phase

- 리액트가 변화한 상태나 props에 따라 어떤 UI가 변경되어야 할지를 결정하는 단계입니다.
- 실제 업데이트가 아닌 변경사항을 가상 DOM에 계산하여 비교합니다.

### commit phase

- 실제 변화한 UI를 DOM에 반영하는 단계입니다.
- 가상 DOM에 계산된 결과를 실제 DOM에 적용하고 변화된 UI를 브라우저에 렌더링합니다.
- 이때 useEffect와 같은 사이드 이펙트를 발생시키는 훅이 실행됩니다.

### 둘의 동기화

- render phase 이후 바로 commit phase를 실행하지 않고 다른 높은 우선순위 작업을 진행합니다.
- 모든 변경 사항이 준비된 상태에서 commit phase로 넘어가기 때문에 render와 commit 단계의 일관성이 유지됩니다.
