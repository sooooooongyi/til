## window.location으로 페이지 이동하기

- 자바스크립트에서 페이지를 이동하기 위해 사용할 수 있는 window 속성, 메소드들이 있다.

### location.href

- 속성
- 웹 브라우저 히스토리에 저장된다. (뒤로 가기)
- 사용자 클릭등의 사용자 인터렉션에 의해 URL을 이동하는 경우 사용한다.

### location.replace()

- 메소드
- 웹 브라우저 히스토리에 저장되지 않아 뒤로가기 시 replace() 호출 페이지로 갈 수 없다.
- 결제 사이트처럼 뒤로가기로 이전 페이지에 가는것을 차단하거나 방문 히스토리를 남기지 않아야할때 사용한다.

### window.open()

- 새 창 띄우기 위한 메소드
- 여러 옵션들이 있음
  - url
  - windowname
  - windowfeatures
  - 등등
    ![스크린샷 2022-03-28 오후 5.33.40.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bc26fd56-4e1f-4009-92d8-3324c8b7af9e/스크린샷_2022-03-28_오후_5.33.40.png)
