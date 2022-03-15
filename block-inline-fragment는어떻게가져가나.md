## block inline fragment는 어떻게 가져가나?

### Geometry → fragment

CSS Rendering엔 크게 두가지 과정이 있다.

(1) 화면의 구역을 나누자!

(2) 나눠진 구역을 채우자!

이때 절대적으로 나눠진 구역을 fragment라고 부른다.

### Block Formatting Contexts

- 부모의 가로 길이를 가득 채운 한줄의 요소
- 계산법
  - x: 0
  - y: (내 앞에 block 요소들의 height 합)
  - width: parent
  - height: (내 안에 있는 block 요소들의 height 합)

### Inline Formatting Contexts

- 나의 콘텐츠 크기 만큼 가로를 차지한다.
- 계산법
  - x: (이전 inline 요소들의 width 합, 대신 부모보다 크면 내려감)
  - y: (이전 줄에 inline 요소들중 가장 height가 큰 요소가 line-height)
  - width: 내 컨텐츠
  - height: 같은 줄 inline 요소들중 가장 height가 큰 요소의 height
- 공백 문자열 없는 문자열은 하나의 inline 요소로 본다. → word-break로 문자 하나하나를 inline으로 판단

### 문자열이 넘치는 경우, BFC와 IFC는 어떻게 동작하나?

#### BFC

![스크린샷 2022-01-18 오후 10.52.01.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8baf79ca-41fe-466a-bfe9-dc8ff0b5c313/스크린샷_2022-01-18_오후_10.52.01.png)

![스크린샷 2022-01-18 오후 10.51.52.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9ad011b6-69d5-44e0-a027-69e387546227/스크린샷_2022-01-18_오후_10.51.52.png)

BFC의 width는 default 값이 부모의 너비다. 위 코드에선 스타일 속성이 있기 때문에 10px을 가진다. fragment는 자식 inline 요소와 상관없기 때문에 빨간 박스의 크기는 자식 요소 크기에 영향을 받지 않는다.

#### IFC

![스크린샷 2022-01-18 오후 10.52.10.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8e78609a-28c0-4fa0-9e9d-1108ab5b37e7/스크린샷_2022-01-18_오후_10.52.10.png)

![스크린샷 2022-01-18 오후 10.51.42.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/72e8c7d2-2d9b-4148-8f2c-75c112ba7463/스크린샷_2022-01-18_오후_10.51.42.png)

IFC의 width는 모든 자식 요소들의 height의 합이다. 그렇기 때문에 inline 요소인 span 태그의 fragment는 자식 요소의 크기 만큼 정해진다.
