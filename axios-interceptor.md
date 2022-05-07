## axios inspector

- 네트워크 응답을 처리하기 전에 결과를 가로챌 수 있다.

### 사용하는 이유

- api 호출할때마다 axios 인스턴스를 생성해야한다.
- 비슷한 헤더값을 갖는 인스턴스가 많다.
- baseurl처럼 중복값이 많다.

### 사용법

- 요청
  ```jsx
  // 요청 인터셉터 추가
  axios.interceptors.request.use(
    function (config) {
      // 요청을 보내기 전에 수행할 일
      // ...
      return config;
    },
    function (error) {
      // 오류 요청을 보내기전 수행할 일
      // ...
      return Promise.reject(error);
    }
  );
  ```
- 응답
  ```jsx
  // 응답 인터셉터 추가
  axios.interceptors.response.use(
    function (response) {
      // 응답 데이터를 가공
      // ...
      return response;
    },
    function (error) {
      // 오류 응답을 처리
      // ...
      return Promise.reject(error);
    }
  );
  ```
