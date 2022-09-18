## Web Vitals

> create-react-app으로 리액트 프로젝트를 만들면 index.js에 자동으로 추가된 `reportWebVitals(console.log);`를 발견할 수 있다. 이건 뭘까?

### Core Web Vitals

웹 페이지 로딩 속도, 모바일 친화성, 세이프 브라우징, 암호화, 방해요소 여부 등과 같은 웹 콘텐츠 이용자의 사용 경험에 영향을 미치는 다양한 측정 가능한 값들 중에서 특별히 강조되는 3가지 Metrics를 의미합니다. `LCP (Largest Contentful Pain), FID (First Input Delay), CLS (Cumulative Layout Shift)`를 말합니다. 이 세 지표는 웹사이트를 방문하는 유저들의 경험을 좌우하는 여러 요소 중 가장 기본이자, 핵심 지표입니다.

### LCP (Largest Contentful Pain)

- 웹 페이지의 로딩 속도에 대한 지표
- 뷰포트의 모든 HTML 요소들이 렌더링 완료되는데까지 걸리는 시간의 길이를 말한다.
- 이미지, 이미지 태그, 비디오 썸네일, CSS가 있는 배경이미지, 단락, 머리글, 목록과 같은 텍스트 요소의 로딩 속도만들 계산합니다.
- Lighthouse, Chrome DevTools, PageSpeed Insight 등의 구글이 제공하는 툴로 측정할 수 있다.
- 2.5s 이하 Good, 4s 이상 Bad

### FID (First Input Delay)

- 사용자간의 상호 작용에 대한 Metric
- 사용자가 웹페이지에 들어와 로딩되고 있는 상태에서 링크를 클릭하거나, 버튼을 탭하는 등의 자바스크립트 기반의 인터렉션을 발생시켰을 때 브라우저는 중요 콘텐츠 요소 로딩이 완료될 때까지 액션 처리를 일정 시간 보류한다.
  → 이때 다음 액션이 가능하게 되는 시간까지의 길이를 측정한 시간이 FID (액션을 처리하는 시간이 아닌, 지연시키는 시간이 얼마인지!)
- TBT (Total Blocking Time) 으로 측정할 수 있다. (사용자가 체감하는 지표이기 때문이다!)
- 100ms 이하 Good, 300ms 이상 Bad

### CLS (Cumulative Layout Shift)

- 비쥬얼 안정성에 대한 Metrics
- 웹페이지에 들어갔을 때 갑작스럽게 발생하는 레이아웃 이동의 정도를 합산 이동 거리라는 개념을 도입해서 만들어낸 지표
- 0.1 이하 Good, 0.1~0.25 Bad

### 기타 요소

- 모바일 친화성
  - 웹 페이지가 모바일 브라우징에 최적화 되어 있는가에 대한 평가
- 세이프 브라우징
  - 페이지에 방문자의 의도를 속이려는, 즉 오해의 여지가 있는 콘텐츠가 있는가? 혹은 악성 코드나 애드 웨어 등이 심겨져 있지 않은가?에 대한 평가
- HTTPS
  - HTTPS를 제공하고 있는가에 대한 평가
- 방해요소
  - 콘텐츠 소비를 방해하는 전면 광고같은 요소가 있는가에 대한 평가

### SEO에 미치는 영향

- 구글 내 연구 결과에 따르면 core web vital의 기준을 충족한 웹페이지의 경우, 방문자의 이탈 가능성이 24% 낮다고 한다.
- 사용자 경험을 개선하기 위해서 중요한 의미를 갖는다.

### Create-React-App에서 측정하기

- CRA는 web-vitals 라이브러리를 자동으로 추가해 웹 애플리케이션의 성능을 쉽게 측정할 수 있게 한다.

```jsx
function sendToAnalytics(metric) {
  const body = JSON.stringify(metric);
  const url = 'https://example.com/analytics';

  // Use `navigator.sendBeacon()` if available, falling back to `fetch()`
  if (navigator.sendBeacon) {
    navigator.sendBeacon(url, body);
  } else {
    fetch(url, { body, method: 'POST', keepalive: true });
  }
}

reportWebVitals(sendToAnalytics);
```

### reference

- [https://create-react-app.dev/docs/measuring-performance/](https://create-react-app.dev/docs/measuring-performance/)
- [https://developers-kr.googleblog.com/2020/05/Introducing-Web-Vitals.html](https://developers-kr.googleblog.com/2020/05/Introducing-Web-Vitals.html)
- [https://www.ascentkorea.com/core-web-vitals/](https://www.ascentkorea.com/core-web-vitals/)
