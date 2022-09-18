## styled-components와 emotion, 무슨 차이가 나나?

- React에서 CSS in JS를 할때 많이 사용하는 라이브러리
- 전반적인 스타일도 같고, 둘다 sass 문법을 사용하기 때문에 스타일 차이가 없다.
- 성능, 용량도 유의미하게 차이나지 않는다.

### emotion의 차별점

- css props
  ```jsx
  <div style={{color: "red"}}/>

  - 인라인 스타일로 클래스를 사용할 수 있다.

  <div css={[style, themes[theme], sizes[size]]} />

  const themes = {
    primary: css`
      color: red;
    `,
    secondary: css`
      color: blue;
    `
  }
  const sizes = {
    small: css`
      fontSize: 0.75rem;
    `,
    medium: css`
      fontSize: 1rem;
    `
  }
  - css 변수를 조립하여 컴포넌트 스타일링을 진행할 수 있다.
  ```
- ssr
  ```jsx
  - ssr에서 별도의 설정 없이 동작이 된다.
  ```
