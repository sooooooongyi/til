## Open Graph

> html 메타 태그중 하나로 링크만으로 html 내용이 무엇인지 미리보기를 제공하는 태그

### 기본 태그

- og:tile - 사이트의 제목
- og:type - 사이트의 종류(video, movie등)
- og:image - 대표 이미지
- og:url - 대표 url

```jsx
<meta property="og:title" content="Test" />
<meta property="og:type" content="website" />
<meta property="og:url" content="https://naver.com" />
<meta property="og:image" content="https://naver.com" />
```

### 옵션 태그

- og:audio - 오디오 파일 url
- og:description - 사이트 설명
- og:locale - 언어 선택
- og:locale:alternate - 다른 언어 종류
- og:site_name - 세부적인 카테고리 레벨
- og:video - 비디오 파일 url

```jsx
<meta property="og:audio" content="http://example.com/bond/theme.mp3" />
<meta property="og:description"  content="개발 즐겁게 합시다." />
<meta property="og:determiner" content="the" />
<meta property="og:locale" content="en_GB" />
<meta property="og:locale:alternate" content="fr_FR" />
<meta property="og:locale:alternate" content="es_ES" />
<meta property="og:site_name" content="Open graph 태그" />
<meta property="og:video" content="http://example.com/bond/trailer.swf" />
```

### 구조 프로퍼티

- og:OBJECT:url - 경로 (이미지, 비디오, 오디오등)
- og:OBJECT:secure_url - SSL의 경로
- og:OBJECT:type - 타입의 종류
- og:OBJECT:width - 너비
- og:OBJECT:height - 높이
- og:OBJECT:alt - 설명

```jsx
<meta property="og:image" content="http://example.com/ogp.jpg" />
<meta property="og:image:secure_url" content="https://secure.example.com/ogp.jpg" />
<meta property="og:image:type" content="image/jpeg" />
<meta property="og:image:width" content="400" />
<meta property="og:image:height" content="300" />
<meta property="og:image:alt" content="A shiny red apple with a bite taken out" />
<meta property="og:video" content="http://example.com/movie.swf" />
<meta property="og:video:secure_url" content="https://secure.example.com/movie.swf" />
<meta property="og:video:type" content="application/x-shockwave-flash" />
<meta property="og:video:width" content="400" /><meta property="og:video:height" content="300" />
<meta property="og:audio" content="http://example.com/sound.mp3" />
<meta property="og:audio:secure_url" content="https://secure.example.com/sound.mp3" />
<meta property="og:audio:type" content="audio/mpeg" />
```
