## JW Player

- JW Player는 Longtail Ad Solutions 사에서 개발한 웹 기반 미디어 재생을 위한 라이브러리 솔루션이다.
- Flash, HTML5를 완벽하게 지원한다.

## 기본 재생 코드

```jsx
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>JW Player</title>
    <script type="text/javascript" src="./jwplayer.js"></script>
  </head>
  <body>
    <div id="myElement">Loading the player...</div>
    <script type="text/javascript">
      jwplayer("myElement").setup({
        file: "http://content.jwplatform.com/videos/HkauGhRi-640.mp4",
        image: "http://www.jwplayer.com/wp-content/uploads/trends.jpg",
        height: 380,
        width: 640,
      });
    </script>
  </body>
</html>
```

- jwplayer.js는 [공식 페이지](https://www.jwplayer.com/)에서 다운로드 가능

## Reference

- [영상 코딩에 필요한 것들 다 포스팅 되어있음](https://ooz.co.kr/105?category=818548)
- [공식 문서](https://www.jwplayer.com/)
