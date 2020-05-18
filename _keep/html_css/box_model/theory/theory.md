### - Box Model

- HTML 모든 요소는 박스 형태로 되어있다.

  - content 범위 말고 margin, border, padding로 구성된다.

    ㄱ. margin : 가장 바깥 -> 다른 요소와의 간격 설정

    ㄴ. border : content 박스의 테두리  -> 이것으로 박스에 테두리를 표시할 수 있다.

    ​       ex) border: 5px solid red;

    ㄷ. padding : content 내용과 border 사이의 공간

​               \< Tip.  width, height 값 설정은 content 영역 크기 설정 \>



###  ** margin, padding 설정

    - margin: 값1     -> 모든 면 margin 값1 할당
    - margin: 값1 값2 -> 상하엔 값1, 좌우엔 값2 할당
    - margin: 값1 값2 값3 -> 상엔 값1, 좌우엔 값2, 하에 값3 할당
    - margin: 값1 값2 값3 값4 -> 순서대로 상 우 하 좌



 ### ** **width, height 설정**

​    width: 값;

​    height: 값;

​    => 해당 크기로 고정

​    max-width: 값;

​    max-height: 값;

​    => 브라우저의 현재 창 크기에 따라 유동적으로 크기를 변동시켜주고,

​          창을 아무리 키워도 설정 값까지만 키워준다.

​          ----> **<u>내용이 content 영역을 벗어나면 "overflow" 되었다고 하며,</u>**

​                  **<u>이는 overflow 속성으로 제어해준다.</u>**

​    min-width: 값;

​    min-height: 값;

​    => 최소 content 영역 크기를 설정해준다.

​         ----> <u>**내용이 content 영역을 벗어나면 알아서 키워준다.**</u>



### ** overflow

- overflow: visible;        -> 디폴트, 삐져나와도 삐져나온대로 보여준다.

- overflow: hidden;       -> 삐져나온 부분은 안 보이게 처리한다.

- overflow: scroll;           -> 삐져나온 부분이 있든 없든, 스크롤을 만들어준다.

- overflow: auto;             -> 삐져나온 부분이 없으면 스크롤 없이,

  ​                                                                          있으면 스크롤을 만들어준다.



### ** border

- 테두리에 선 그을 때 주로 쓰이는 속성



ㄱ. 4면에 같은 스타일 적용 예시 코드

```html
<style>
    .p1 {
        border: 2px solid blue;
    }
</style>
<!-- 줄 굵기, 줄 형태, 줄 색상 순 값 할당
     값 부여 순서는 상관 없지만 관례상 저렇게 주로 쓴다. -->
<!-- dotted 는 점선
     dashed 는 파선 -->

<!-- 아래는 위와 같은 설정 -->
<style>
    .p1 {
        border-width: 2px;
        border-style: solid;
       	border-color: blue;
    }
</style>
```

ㄴ. 각 면에 다른 스타일 적용 예시 코드

```html
<style>
    .p1 {
        border-top: 2px solid blue;
        border-bottom: 3px dashed red;
        border-left: 5px dotted green;
    }
</style>
```

ㄷ. 테두리 없애기

```html
<style>
    .p1 {
        border: none;
        /* border: 0; 위와 동일*/
    }
</style>
```



## *** 박스를 꾸미는 기타 방법들

1. 둥근 모서리

   border-radius: 값;     -> 값이 커질수록 모서리가 동그래진다.

2. 배경색

   background-color: 값;     -> content 영역 + margin 영역, 

   ​                                                즉 border 안쪽 영역을 해당 색으로 설정 

   

   > <u>Tip. background-color: transparent;     -> 해당 영역을 투명하게 설정.</u>

   > ​                                                                         <u>현 박스 바깥 색깔을 그대로 받아들인다.</u>

   > ​                                                                     -> 디폴트 설정이지만, 명시적으로 써주기도 한다.

   

3. 그림자

   box-shadow: none;     -> 디폴트 설정, 그림자 없음

   box-shadow: 10px 10px;    -> 왼쪽 값이 커지면 커질수록 우측으로 길어지고,

   ​                                                    우측 값이 커지면 커질수록 아래로 길어진다.

   ​                                                    음수 값을 주면 우측이 아닌 좌측, 아래가 아닌 위에 그림자가 생긴다.

 

​       box-shadow: 10px 10px red;  -> 그림자 색상까지 설정

​       box-shadow: 10px 10px 5px red;   -> 세 번째 값인 5px는 그림자의 흐림도를 설정해준 것

​       box-shadow: 10px 10px 5px 0px red;   -> 네 번째 값인 0px는 그림자의 굵기를 설정해준 것

​                                                                                0이 기본 크기, 더 작게 하려면 음수 할당



### ** box의 범위?

- 기본적으로

  box-sizing: content-box;

  설정이 되어있다.

  width, height 설정은 content-box 를 설정하는 것.

- border 까지 포함하여 width, height를 설정해주고 싶은 경우가 많다.

  content 까지가 아니라 box 크기 자체를 제어해주고 싶은 경우가 많으므로,

  이 때,

  box-sizing: border-box;

  설정해주면 된다.



### ** background-image

​	background-image: url("이미지 경로");

​	background-repeat: no-repeat;       => 이래야 사진이 반복되지 않는다.

​    background-size: 100% 50px;          => % 지정해줘서 사진이 항상 꽉 채워짐.

​                                                                        but.. 원래 사진 비율이 뭉개질 수 있다.

​    background-size: cover;                    => 원래 사진 비율 유지, 단 그러므로 사진이 잘릴 수 있다.

​    background-position: right bottom;    => 사진 비율을 유지해야해서 잘리는 상황일 때,

​                                                                            어떤 부분을 살릴지 결정 -> 왼쪽의 경우 왼쪽, 위쪽이 잘린다



​    Tip. [after]를 사용해 배경 이미지만 투명도를 조절할 수도 있다.

​            => 이건 실 사용 때.. 구글링 해보자.. (( 03.20 ))