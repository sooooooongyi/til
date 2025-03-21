## webpack, rollup과 같은 번들러는 왜 필요한지 설명해주세요.

- 번들러는 다양한 파일과 모듈을 하나의 배포 가능한 번들로 묶는 역할을 합니다.
- 네트워크 요청 성능을 개선하기 위해 사용합니다.
  - 다수의 개별 파일에 대해 모두 네트워크 요청을 수행한다면, 성능에 부정적인 영향이 있을 수 있습니다.
  - 다수의 파일을 소수의 파일로 묶어 네트워크 요청을 최적화합니다.
- 트랜스파일링을 통해 더 효율적이고 호환성 있는 애플리케이션을 만들 수 있습니다.
  - Dead Code Elimination, Tree Shaking과 같은 방법을 통해 불필요한 코드와 모듈을 제거해 번들 크기를 줄이고 로딩 성능을 개선합니다.
  - 최신 자바스크립트 문법과 기능을 구형 브라우저에서도 실행 가능하도록 변환시킵니다. (ES6이상을 ES5로 변환)
