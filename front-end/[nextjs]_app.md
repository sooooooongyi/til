# \_app 사용법

> nextjs를 공부하는 도중 리액트와 다른 점을 발견했고 정리가 필요하다.

- App 컴포넌트는 모든 페이지의 공통 페이지 역할을 한다.
- App 컴포넌트를 이용하면 `페이지들의 공통된 레이아웃`, `페이지를 탐색할 때 상태유지`, `추가 데이터를 페이지에 주입`, `글로벌 CSS 추가`를 할 수 있다.

```jsx
const MyApp = ({ Component, pageProps }) => {
  return (
    <>
      <Component {...pageProps} />
      <style jsx global>{`
        body {
          margin: 0;
        }
      `}</style>
    </>
  )
}

export default MyApp
```

- 위 \_app 예시 코드에서 Component는 불러오게 되는 `페이지`를 받게 된다.
- Component는 pageProps를 `props`으로 받게 된다.
- pageProps는 pages 안의 파일에서 `getServerSideProps`, `getStaticProps`, `getInitialProps`로 페이지에 전달해주는 props다.
