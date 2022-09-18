## redux-thunk

- redux-thunk는 리덕스에서 비동기 작업을 처리할 때 가장 많이 사용하는 미들웨어입니다.
- 이 미들웨어를 사용하면 액션 객체가 아닌 함수를 디스패치 할 수 있다.
- 함수를 디스패치 할 때에는 함수에서 dispatch와 getState를 파라미터로 받아와야하는데 이 함수를 만들어주는 함수를 thunk라고 부른다.
- thunk 함수 예시
  - 원래 dispatch({})를 통해 바로 스토어를 갱신하게 끔 동작한다.
  - 중간에 thunk 함수를 두고 그 함수에서 dispatch, getState해서 원하는 로직에 맞게 dispatch를 하게끔 한다.

```jsx
const getComments = () => (dispatch, getState) => {
  // 이 안에서는 액션을 dispatch 할 수도 있고
  // getState를 사용하여 현재 상태도 조회 할 수 있습니다.
  const id = getState().post.activeId;

  // 요청이 시작했음을 알리는 액션
  dispatch({ type: 'GET_COMMENTS' });

  // 댓글을 조회하는 프로미스를 반환하는 getComments 가 있다고 가정해봅시다.
  api
    .getComments(id) // 요청을 하고
    .then((comments) =>
      dispatch({ type: 'GET_COMMENTS_SUCCESS', id, comments })
    ) // 성공시
    .catch((e) => dispatch({ type: 'GET_COMMENTS_ERROR', error: e })); // 실패시
};
```
