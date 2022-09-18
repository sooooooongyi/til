## text-overflow

- white-space를 이용해 줄 바꿈을 하지 않을 때 넘치는 텍스트를 어떻게 처리할 수 있나?
- text-overflow는 `overflow: hidden, scroll, auto` 이면서 `white-space:nowrap` 인 경우에 적용됩니다.

### text-overflow: clip

- 넘치는 텍스트를 잘라버립니다.
  ![스크린샷 2022-04-15 오전 11.22.44.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b83111b0-40cb-48fa-8d1b-13f4eeced371/스크린샷_2022-04-15_오전_11.22.44.png)

### text-overflow: ellipsis

- 잘리는 부분에서 말 줄임표가 붙습니다.
  ![스크린샷 2022-04-15 오전 11.22.28.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8173dce6-593a-45e9-8105-c1d25e200c9a/스크린샷_2022-04-15_오전_11.22.28.png)
