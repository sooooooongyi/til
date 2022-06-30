## [chapter1] this라나 뭐라나

- this는 모든 함수 스코프 내에 자동으로 설정되는 특수한 식별자로 경험 많은 자바스크립트 개발자도 정확히 무엇을 가리키는지 짚어내기가 만만치 않다.

### 1.2 헷갈리는 것들

- this는 자기 자신이다? → 아니다!
  - this로는 자기 참조를 할 수 없다.
- this는 어떤식으로도 함수의 렉시컬 스코프를 참조하지 않는다.
  - 스코프 객체는 자바스크립트 구현체인 “엔진"의 내부 부품이기 때문에 일반 자바스크립트 코드로는 접근하지 못한다.

### 1.3 this란 무엇인가?

- this는 작성 시점이 아닌 런타임 시점에 바인딩 되며 함수 호출 당시 상황에 따라 콘텍스트가 결정된다.
- 함수 선언 위치와 상관없이 this 바인딩은 오로지 어떻게 함수를 호출했느냐에 따라 정해진다.
- 함수를 호출하면 실행 콘텍스트가 만들어진다.
  - 여기에 함수가 호출된 콜스택과 호출방법, 전달된 인자 등 정보가 담겨있다.
  - this 레퍼런스는 그중 하나! 함수가 실행되는 동안 사용할 수 있다.