## React-Router-Dom

- 기존의 <a> 태그를 이용한 방식은 URL 변경 시 새로고침 되며 모든 페이지를 reload 하여 로드시간이 걸린다. 하지만 React의 react-router-dom은 Router를 이용해 새로고침이 아닌, 변경된 소스만 바꿔도록해 속도가 빠르다.

## React Router: 3 Primary Categories

- Router
  - <BrowserRouter>
  - <HashRouter>
- Router Matcher
  - <Router>
  - <Switch>
- Navigation
  - <Link>
  - <NavLink>
  - <Redirect>

## Router

- <BrowserRouter>, <HashRouter>의 주요 차이점은 URL 저장 방식과 웹 서버 통신 방식이다.
- <BrowserRouter>은 regular URL path에 대한 라우팅을 제공한다.
- <HashRouter>는 hash를 활용한 라우터다. 주소의 형식을`http://example.com/#/your/page` 이런식으로 사용한다.

## Router Matcher

- 현재 URL에서 <Switch>의 자식 <Route> 중 일치하는 것을 찾아 렌더링한다.
- 최초 매칭되는 Route를 찾으면, 다른 것들을 모두 무시한다.
- 잘 사용하기 위해서 `특정한 URL을 위에, 덜 특정한 것을 아래`에 적어야한다.

```jsx
import React from "react";
import ReactDOM from "react-dom";
import { BrowserRouter as Router, Switch, Route } from "react-router-dom";

function App() {
  return (
    <div>
      <Switch>
        {/* If the current URL is /about, this route is rendered
            while the rest are ignored */}
        <Route path="/about">
          <About />
        </Route>

        {/* Note how these two routes are ordered. The more specific
            path="/contact/:id" comes before path="/contact" so that
            route will render when viewing an individual contact */}
        <Route path="/contact/:id">
          <Contact />
        </Route>
        <Route path="/contact">
          <AllContacts />
        </Route>

        {/* If none of the previous routes render anything,
            this route acts as a fallback.

            Important: A route with path="/" will *always* match
            the URL because all URLs begin with a /. So that's
            why we put this one last of all */}
        <Route path="/">
          <Home />
        </Route>
      </Switch>
    </div>
  );
}

ReactDOM.render(
  <Router>
    <App />
  </Router>,
  document.getElementById("root")
);
```

## Navigation

- URL을 이동시키기 위해 <Link> 컴포넌트를 사용하는데, HTML엔 <a>로 렌더링된다.
- <NavLink>는 특별한 <Link>로 active 클래스를 줄 수 있다.

```jsx
<NavLink to="/react" activeClassName="hurray">
  React
</NavLink>

// When the URL is /react, this renders:
// <a href="/react" className="hurray">React</a>

// When it's something else:
// <a href="/react">React</a>
```

- <Redirect> 는 강제로 이동하고 싶을 때 사용할 수 있다. to prop에 원하는 주소를 입력한다.

## Reference

- [react-router-dom 공식문서](https://v5.reactrouter.com/web/guides/primary-components)
