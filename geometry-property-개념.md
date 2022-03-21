## geometry property 개념

> 스크롤 이벤트 관련 코드를 분석하다가 위치를 잡기위해 쓰여진 client ~~, offset~~, scroll~ 의 차이점을 알아보자!

![스크린샷 2022-03-21 오후 2.53.57.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0be8fef0-9355-43dc-8b85-13bb1059d716/스크린샷_2022-03-21_오후_2.53.57.png)

### scrollHeight(Width)

- 눈에 보이지 않는 영역까지 포함한 전체 content + padding 크기 값
- 요소 콘텐츠의 총 높이를 나타내고 바깥으로 넘쳐서 보이지 않는 콘텐츠도 포함합니다.
- scrollTop은 브라우저 상단에서 현재 스크롤까지 이동한 값을 나타내는 코드

### clientHeight(Width)

- 눈에 보이는 content + padding 크기의 값
  ![스크린샷 2022-03-21 오후 2.52.58.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/06d09571-e334-4b8d-91c4-682d8fdd2c95/스크린샷_2022-03-21_오후_2.52.58.png)

### offsetHeight(Width)

- 눈에 보이지 content + padding + border + scrollbar의 값
- offsetTop은 position model에 따라 정해진 offset parent 를 기준으로 삼는다.
