## styled-component-theme-provider

- styled-component에선 contextAPI를 사용해 공통적인 CSS를 관리할 수 있도록 한다.
- 이때 theme provider를 사용하는데, 모든 리액트 컴포넌트에게 theme 속성을 전달하는 역할을 수행한다.

```jsx
import React from "react";
import { ThemeProvider } from "styled-components";

const theme = {
  // css style
};

const RootComponent = () => {
  return <ThemeProvider theme={theme}>{/* components */}</ThemeProvider>;
};
```

- 위 코드처럼 하위 컴포넌트들이 props으로 넘어간 css theme를 사용할 수 있게 된다.

## 적용

- theme.js로 공통적인 스타일을 작성한다.

```jsx
import styled from "styled-components";

// 반응형 디자인을 위한 픽셀 컨버팅 함수
const pixelToRem = (size) => `${size / 16}rem`;

// font size를 객체로 반환해주자.
const fontSizes = {
  title: pixelToRem(60),
  subtitle: pixelToRem(30),
  paragraph: pixelToRem(18),
};

// 자주 사용하는 색을 객체로 만들자.
const colors = {
  black: "#000000",
  grey: "#999999",
  green: "#3cb46e",
  blue: "#000080",
};

// 자주 사용하는 스타일 속성을 theme으로 만들어보자.
const common = {
  flexCenter: `
    display: flex;
    justify-contents: center;
    align-items: center;
  `,
  flexCenterColumn: `
    display: flex;
    flex-direction: column;
    justify-contents: center;
    align-items: center;
  `,
};

// theme 객체에 감싸서 반환한다.
const theme = {
  fontSizes,
  colors,
  common,
};

export default theme;
```

- 컴포넌트에서 가져와 사용한다.

```jsx
import React from "react";
import styled, { ThemeProvider } from "styled-components";
import theme from "./theme";

const Container = styled.div`
  width: 100vw;
  height: 100vh;
  ${({ theme }) => theme.common.flexCenterColumn};
`;

const Title = styled.h1`
  font-size: ${({ theme }) => theme.fontSizes.title};
  color: ${({ theme }) => theme.colors.grey};
`;

const App = () => {
  return (
    <ThemeProvider theme={theme}>
      <Container>
        <Title>Styled-Components</Title>
      </Container>
    </ThemeProvider>
  );
};
```

## Reference

- [styled-component theme provider](https://wonit.tistory.com/366)
