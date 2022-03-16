## 프론트엔드 개발 연습용 가짜 API 서버 만들기

- 우선 데이터 파일을 준비한다.

```jsx
// data.json
{
  "posts": [
    {
      "id": 1,
      "title": "리덕스 미들웨어를 배워봅시다",
      "body": "리덕스 미들웨어를 직접 만들어보면 이해하기 쉽죠."
    },
    {
      "id": 2,
      "title": "redux-thunk를 사용해봅시다",
      "body": "redux-thunk를 사용해서 비동기 작업을 처리해봅시다!"
    },
    {
      "id": 3,
      "title": "redux-saga도 사용해봅시다",
      "body": "나중엔 redux-saga를 사용해서 비동기 작업을 처리하는 방법도 배워볼 거예요."
    }
  ]
}
```

- 해당 명령어를 입력한다.

```jsx
npx json-server ./data.json --port 4000
```

- [localhost:4000](http://localhost:4000) 으로 접속하고 axios,fetch등을 이용해 데이터를 불러온다.

```jsx
const { data } = axios.get('http://localhost:4000/~);
```

- 전역 설치가 필요한 경우 아래 명령어를 입력한다.

```jsx
$ yarn global add json-server
$ json-server ./data.json --port 4000
```

## reference

- [https://react.vlpt.us/redux-middleware/08-json-server.html](https://react.vlpt.us/redux-middleware/08-json-server.html)
