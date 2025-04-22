## Stacking Context에 대해 설명해주세요.

- 가상의 z축을 상정하여 HTML 요소들을 3차원으로 개념화한 것
- HTML요소는 DOM순서에 따라 쌓입니다.
- position 속성이 적용되어있는 요소들은 z-index 값에 따라 쌓입니다.
- 하지만, 특정 조건이 충족되면 새로운 쌓임 맥락이 생성됩니다.
  - position 속성이 relative 또는 absolute이고, z-index가 auto가 아닌 경우
  - position 속성이 fixed 또는 sticky인 경우
  - display가 flex 또는 grid 이고, z-index가 설정된 경우
  - opacity 값이 1미만인 경우
  - transform, filter, backdrop-filter 등의 속성이 적용되는 경우
