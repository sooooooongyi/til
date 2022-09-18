## react-slick

- 리액트 프로젝트에서 캐러셀을 쉽게 구현해주는 모듈

### 설치 및 추가 설정

```jsx
npm install react-slick
```

- import .css를 위해 추가적인 모듈도 설치해준다.

```jsx
npm install slick-carousel
```

- typescrpit로 작성할 것이기 때문에 추가적인 type도 설치해준다.

```jsx
npm i @types/react-slick
```

- 이 파일들을 불러와 슬라이더를 만든다.

```jsx
import 'slick-carousel/slick/slick.css';
import 'slick-carousel/slick/slick-theme.css';
```

### 사용법

- SimpleSlider는 Settings 값을 넣어 원하는 형태로 사용할 수 있다.

```jsx
import React from 'react';
import Slider from 'react-slick';
import Card from '../card/Card';
import 'slick-carousel/slick/slick.css';
import 'slick-carousel/slick/slick-theme.css';

interface SimpleSliderProps {}

const SimpleSlider = (props: SimpleSliderProps) => {
  const settings = {
    dots: true,
    infinite: true,
    speed: 100,
    slidesToShow: 1,
    slidesToScroll: 1,
  };
  return (
    <div>
      <Slider {...settings}>
        <Card></Card>
        <Card></Card>
        <Card></Card>
        <Card></Card>
        <Card></Card>
      </Slider>
    </div>
  );
};

export default SimpleSlider;
```

- Card

```jsx
import React from 'react';
import styled from 'styled-components';

interface CardProps {}

const Card = (props: CardProps) => (
  <CardWrapper>
    <CardContent />
  </CardWrapper>
);

export default Card;

const CardWrapper = styled.div`
  width: 100%;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
`;

const CardContent = styled.div`
  width: 80%;
  height: 100%;
  background-color: pink;
`;
```

### 결과

- 간단한 슬라이더를 만들 수 있다.

![스크린샷 2022-03-21 오후 5.44.03.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2cebdf4d-97e9-41d7-a947-fe248fa58a20/스크린샷_2022-03-21_오후_5.44.03.png)
