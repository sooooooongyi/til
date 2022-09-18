## background vs background-color

> css 코드를 보면 background 색상을 지정하는데 두가지 방법으로 작성되어있다. 무엇이 다르고, 무엇을 쓸까?

### background-color

- 속성 이름 그대로, 배경의 ‘색상'을 지정할 수 있다.

### background

- 속성 이름 그대로, 배경에 대한 설정을 할 수 있다.
- 사용할 수 있는 속성
  - color
  - image
  - repeat
  - attachment
  - position
- 사용 예시
  ```jsx
  .root {
  	background: #fff; // background-color를 설정
  	background: url('~~.png') // background-image를 설정
  	background: no-repeat // background-repeat를 설정

  	background: #fff url('') no-repeat; // 띄어쓰기로 구분해 여러 속성을 지정할 수 있다.
  }
  ```
