## 📝 key를 사용해야하는 이유

> **왜 궁금한가 |** react, vue를 배우면서 리스트를 렌더링할 때 콘솔에 찍히는 key에 관련된 문구를 본 적이 있다. 쓰면 좋다고는 하는데 왜? 얼마나 좋은가? 가 궁금해 탐구해보았다.

### key가 꼭 필요한 react의 동작

```javascript
function App() {
    const [list, setList] = useState(initialList)
    const initialList = [
        {
            id: 1,
            name: 'item1'
        },
                {
            id: 2,
            name: 'item2'
        },
                {
            id: 3,
            name: 'item3'
        }
    ]

    const handlerClick() => {
        newList = {
            id: 4,
            name: 'item4'
        }
        setList(preState => {
            newList,
            ...preState
        })
    }

    return (
        <div>
        {list.map(item => <div>{item.name}</div>)}
        <button onClick={handlerClick}>Click Me!</button>
        </div>
    )
}

```

위의 예시는 App 컴포넌트에서 list를 map 함수를 통해 렌더링을 한다. 그리고 Click Me! 버튼을 클릭했을 때 새로운 newList를 기존 리스트의 가장 맨 첫번째 item으로 추가해 다시 렌더링하는 코드이다.

위 코드는 물론 잘 동작하는 코드지만, 렌더링의 과정을 보면 어딘가 이상한 부분이 생긴다. 바로 클릭을 누르는 즉시 리스트의 가장 첫 부분 새로운 item이 들어가는 것이 아닌 맨 마지막에 들어가는 것이다. 하지만 렌더링은 첫번째로 잘 들어가있는 것을 확인할 수 있다. 어떻게 된 일인가?

정답은 (1) 버튼을 클릭한다. (2) 리스트에 새로운 item를 넣는다. (맨마지막에!) **(3) 그리고 react에서의 list와 순서를 맞춰보고 다시금 업데이트한다.** 이 순서대로 동작하기 때문에 결과적으로 맨 앞에 보여지게 된다.

여기서 짚고 넘어가고 싶은 부분은 (3) react와 순서를 맞춰보는 과정이다. react는 두 리스트를 비교해 변경 사항이 있을 때 업데이트를 한다. 이때 리스트가 key를 가지고 있지 않다면 모든 아이템들을 비교해 리스트를 다시 렌더링한다. 즉, 어디서 어떤 아이템이 변경되었는지 알 수 없기 때문에 처음부터 끝까지 모든 리스트 아이템을 업데이트하게 된다. 이는 성능상에 문제가 생길 수 있고 업데이트하는 과정에서 상태에 대한 손실이 발생할 수 있다.

```javascript
return (
  <div>
    {list.map((item) => (
      <div key={item.id}>{item.name}</div>
    ))}
    <button onClick={handlerClick}>Click Me!</button>
  </div>
);
```

이를 해결하기 위해선 아이템을 렌더링할때 key를 함께 넣어주어야한다. key를 넣음으로써 react는 이전 리스트와 비교에 어떤 아이템이 추가되거나 삭제되었는지 확인할 수 있고 그 아이템에 대한 부분만 업데이트하기 때문에 효율적으로 처리할 수 있다.

주로 key 값으론 아이템 prop의 id나 반복문의 index를 사용하곤 하는데, index는 문제점을 가질 수 있다. 처음 또는 중간에 아이템 삽입, 삭제 등으로 index는 바뀔 수 있기 때문에 react가 결국 변화한 index가 어떤 아이템인지 인지할 수 없다.

### 그래서?

반복 렌더링을 할 땐 꼭 key값을 넣어주자! key값을 넣어줄 땐 id나 고유한 값들을 넣어주고, index는 피해야한다.
