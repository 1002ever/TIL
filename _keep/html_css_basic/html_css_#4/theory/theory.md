#### * 텍스트 색

```html
    <style>
        h1 {
            color: orange;
        }
        h2 {
            color: rgb(97, 249, 107);
            /* color: #61F96B */
        }
    </style>
```

  ㄱ. 색 이름을 주기

  ㄴ. rgb 값 주기

  ㄷ. 1진수 값 주기

​        등등..

  ##### Tip. 투명도 설정?

- rgba 값을 줄 때, a 값에 해당하는 것이 투명도

- hex 코드 6글자 뒤에 두 자리 수를 추가해주면 투명도를 설정할 수 있다.

  (( 00 투명 ~ FF 불투명 ))





#### *** 몇 가지 텍스트 스타일링



  (1) 굵기   ( 주의, 100 단위만 가능.

​                     ex) <u>110 값을 주면 디폴트 굵기로 적용된다.</u> 

​                    <u>또, 폰트나 브라우저 마다 지원하는 굵기 값이 다르다.</u>

​                    사용 전에 지원하는 굵기 값인지 확인 필수 )

​    font-weight: 값;

  (2) 크기

​    font-size: 값;

  (3) 정렬

​    text-align: center;

​                       right;

​                       left;

​                       등..

  (4) text-decoration: underline;

​                                     overlline;

​                                     line-through;

​                                     none;               =>  보통 a 태그에 적용하여, 기본적으로 그어진 밑줄을 지워준다.

​      Tip. 밑줄 색깔 바꾸려면

​             text-decoration-color: 색상;



### *** em과 rem의 차이, 용례

https://webdesign.tutsplus.com/ko/tutorials/comprehensive-guide-when-to-use-em-vs-rem--cms-23984



#### ** content area / line height 차이

- line-height: normal;    =>  content area 만큼 line height 설정

- line-height: 값;             => 값 만큼 line height 설정.

  ​                                            content area 보다 클 경우 줄 간격이 넓어지고

  ​                                            content area 보다 작을 경우 content area 영역이 짤릴 수 있다.





#### ** 폰트 설정

\* 글꼴 예시

![](글꼴.jpg)



\* 주의사항

- 글꼴 이름이 여러 단어이면 " " 로 묶어줘야 한다.

- 모든 글꼴이 모든 환경에서 지원하는 것은 아니다.

  => 여러 글꼴로 설정해줘야 안전한 설정, 최종 글꼴은 글꼴의 종류 탭을 지정해줄 것.

  ​     *<u>아래 코드에서 Times New Roman과 Times가 없다면 serif 글꼴 중 하나를 택해 설정한다.</u>*

   ex) font-family: "Times New Roman", Times, serif



#### * 페이지 내에서 폰트를 제공해주기

- 구글 폰트

  ㄱ. fonts.google.com 에 접속

  ㄴ. 맘에 드는 폰트 선택

  ㄷ. STANDARD @ IMPORT 란에 있는 link 태그 복사

  ㄹ. head 태그에 붙여넣기

  ㅁ. 이제부터 Specify in CSS에 나온 것 처럼 font-family에 적용 가능

![](구글폰트.jpg)



```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>Test</title>
    <link href="https://fonts.googleapis.com/css?family=Yeon+Sung&display=swap" rel="stylesheet">
    <style>
        h1 {
            font-family: 'Yeon Sung', cursive;
            color: orange;
        }
        h2 {
            color: rgb(97, 249, 107);
            /* color: #61F96B */
        }
    </style>
</head>
<body>
    <h1>텍스트 색 변경!</h1>
    <h2>rgb 값으로 색 주기!</h2>
</body>
</html>
```



### * 폰트 파일로 적용

```html
<!-- css -->

@font-face {
    src: url("fonts/BMJUA_ttf.ttf");
    font-family: "BmJua";
}

p {
    font-family: "BmJua";
}

<!-- html -->

<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <link href="style.css" rel="stylesheet">
    <title>Font file</title>
</head>
<body>
    <p>주아체 적용~!</p>
</body>
</html>
```



#### ** span 태그

- div 태그의 inline 버전

  -> 문단 내 특정 요소를 span 태그 씌워주면

  ​    문단의 layout에 영향을 주지 않으면서 스타일 적용이 가능해진다.

