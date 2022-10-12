# \_document 사용법

> 리액트에서 사용하지 않는 \_document 정리

- 사용자 정의 Document는 일반적으로 응용 프로그램 <html> 및 <body> 태그를 보강하는 사용한다.
- Document를 이용해 <title>, <description>, <meta> 등 프로젝트의 정보를 제공하는 HTML 코드를 작성할 수 있다.
- 폰트나 외부 api, cdn 등을 불러올 수 있다.
- CSS-in-JS의 서버 사이드 렌더링을 위한 설정을 할 때 사용한다.

```jsx
import Document, { Html, Head, Main, NextScript } from "next/document"

class MyDocument extends Document {
  render() {
    return (
      <Html lang="ko">
        <Head>
          <meta name="title" content="" />
          <meta name="description" content="" />
          <link href="" rel="" />
        </Head>
        <body>
          <Main />
          <NextScript />
        </body>
      </Html>
    )
  }
}

export default MyDocument
```
