## axios timeout

> API 호출이 무한히 로딩되면 어떡할까?

axios는 기본적으로 API을 호출하면 응답이 올때 까지 기다린다. 하지만 API 응답이 무한히 오지 않으면 무한히 기다려야할까?

이를 방지하기 위해 axios instance에 timeout를 추가할 수 있다.

```jsx
const instance = axios.create({
  timeout: 1000, // 1초 안에 응답이 없다면 요청을 최소하고 에러를 던지자!
});
```

- axios 객체에 옵션으로 간단히 설정할 수 있다.

그렇다면 timeout이 지나 취소된 후 어떻게 처리할까?

바로 에러를 throw 하게되고 만약 에러를 처리하는 try ~ catch문이 있다면 catch문에 걸리게 된다.

### 예시 코드

```jsx
const instance = axios.create({
	timeout: 1000
})

const apiCall = async () => {
	try {
		const res = await instance.get(...) // api 호출
		console.log(res.data)
	} catch (error) {
		// timeout error 처리
	}
}
```
