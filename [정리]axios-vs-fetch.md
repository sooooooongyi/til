# Axios vs Fetch

> 네트워크 통신을 위한 함수, 무엇을 쓰는 것이 좋을까?

## 공통점

- 프로미스 기반의 HTTP 클라이언트이기 때문에, 프로미스를 반환한다.

## Fetch

- 모던 브라우저에 탑재되어 있어 별도의 설치가 필요없다.
- 그렇기에 nodejs에서도 사용할 수 있다.
- .then() 메소드로 결과를 반환 받을 수 있지만, JSON 데이터 형식이 아니기 때문에 .json() 메소드로 변환할 수 있다. (프로미스를 2개 반환)
- 데이터를 보낼 때 JSON 형식으로 변환해 보내야한다.
- 요청 헤더를 따로 content-type default : application/json로 지정해야한다.
- 404 에러나 기타 HTTP 에러 발생시 reject를 반환한다. (ok 값으로 커스텀 에러를 던진다.)
- abort() 메소드로 요청을 중단시킬 수 있고 setTimeout에 콜백을 사용할 수 있다.
- axios보다 빠르다. (아주 조금?)

## Axios

- 네트워크 통신을 위한 third-party 라이브러리이기 때문에 설치가 필요하다.
- JSON 데이터 형식으로 반환한다. responseType으로 명시도 가능하다.
- 데이터를 따로 JSON 형식으로 변환하지 않아도 가능하다.
- content-type default가 application/json이다.
- 응답 상태코드가 200번 이상이면 reject를 반환한다. (response, request 프로퍼티를 갖는 error object를 반환받는다.)
- timeout 만큼 요청이 지연되면 요청을 취소하고 에러를 전달한다.
