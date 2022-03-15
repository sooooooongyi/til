## TypeScript에서 DOM 접근하기

### 기본 예제

![스크린샷 2022-01-13 오후 10.14.58.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/50701099-4e17-4ee1-9fd7-78a9ae999d0d/스크린샷_2022-01-13_오후_10.14.58.png)

- getElementById, createElement 함수의 반환값은 HTMLElement | null
- null인 경우, appendChild 함수 호출이 안된다 → 안전하지 않다!
- 옵셔널 체이닝으로 null에 대한 대응 가능

### 정답은 HTMLElement!

결국 `타입 단언` 을 통해 이 문제를 해결할 수 있다. 타입 단언이란, 개발자가 명시적으로 타입을 지정해주는 것! 타입스크립트가 스스로 해석하는 것이 아니기 때문에 지양해야하지만, DOM API 조작에선 많이 사용한다.

![스크린샷 2022-01-13 오후 10.40.36.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/22e4a55a-2e4e-4495-b7aa-1a3698f59822/스크린샷_2022-01-13_오후_10.40.36.png)

`as (타입이름)` 으로 바꿈으로써 null에 대비하기 위한 분기문을 사용하지 않아도 됩니다.
