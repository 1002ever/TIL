#### \# 클래스와 ID

- 일종의 이름 같은 것

- 클래스 명은 한 태그에 여러 개 부여 가능

  => 여러 스타일을 적용할 수 있다는 의미

- 클래스는 style 선택자에서 .클래스명

  ID는 style 선택자에서 #ID

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>id/class example</title>

    <style>
        .big-blue-text {
            font-size: 64px;
            color: blue;
        }
        .centered-text {
            text-align: center;
        }
        #best-text {
            color: orange;
        }
    </style>
</head>
<body>
    <h1 id="best-text">Heading 1</h1>
    <h2>Heading 2</h2>

    <p>첫 번째 문단</p>
    <p>두 번째 문단</p>
    <p class="big-blue-text centered-text">세 번째 문단</p>
    <p>네 번째 문단</p>
</body>
</html>
```



##### ** 그럼 클래스와 ID는 뭐가 달라?

--> 클래스는 중복 사용이 가능 => 여러 태그가 같은 클래스 명을 갖어도 된다.

​                                                          또 한 태그가 여러 클래스 명을 갖을 수 있다.

​      ID는 중복 사용이 불가능 => 여러 태그가 같은 ID를 가지면 안 된다.

​                                                       (( HTML은 문법적으로 혀용, 

​                                                           단 JS와 연동 시 그 중 하나만 스타일 적용되므로 문제 발생 ))

​                                                      또 한 태그는 하나의 ID만 가질 수 있다.

​      ====> <b>여러 요소를 꾸미고 싶으면 class, 한 요소만 꾸미고 싶으면 id</b>



##### ** class 와 id 태그 중첩 사용 시 우선 적용되는 것은?

-- 답변 참고 링크 : https://www.codeit.kr/learn/courses/web-publishing/542

  ==> <u><i>공부 마다 읽어보기</i></u>



### \#  \<div> 태그?

- 블록 단위로 구분하기 위한 의미 없는 태그.
- 어떤 기능들 단위로 태그들을 묶어 블록 단위를 구성하면 -> **가독성 증가**

- 해당 블록에 id나 class를 정하여 그 블록만 특정 스타일 적용하는 것이 가능

   \*** \<span> 태그는 div 태그의 inline 버전이라고 보면 된다.



\*** Tip. 가운데 정렬?

ㄱ. 텍스트 정렬

text-align: center;

ㄴ. 블록을 가운데로 배치

(1) margin: 0 auto;

(2) margin-left: auto;

​     margin-right: auto;   



#### \# CSS 스타일 파일로 적용

​    ==> \<link href="css 파일 경로" rel="stylesheet">

```html
<!-- HTML 파일 -->
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>id/class example</title>
    <link href="css/style.css" rel="stylesheet">
</head>
<body>
    <h1 id="best-text">Heading 1</h1>
    <h2>Heading 2</h2>

    <p>첫 번째 문단</p>
    <p>두 번째 문단</p>
    <p class="big-blue-text centered-text">세 번째 문단</p>
    <p>네 번째 문단</p>
</body>
</html>

<!-- css 폴더 내 css 파일 -->
.big-blue-text {
    font-size: 64px;
    color: blue;
}
.centered-text {
    text-align: center;
}
#best-text {
    color: orange;
}

```



#### \# CSS를 style 속성으로 적용

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>id/class example</title>
    <link href="css/style.css" rel="stylesheet">
</head>
<body>
    <h1 id="best-text">Heading 1</h1>
    <h2>Heading 2</h2>

    <p>첫 번째 문단</p>
    <p>두 번째 문단</p>
    <p class="big-blue-text centered-text">세 번째 문단</p>
    <p style="color: red;">네 번째 문단</p>
    <!-- 네 번째 문단만 빨간색 글자로 표시 -->
</body>
</html>
```



##### ** Tip. CSS는 파일로 적용하는 것이 가장 권장된다.

- html 문서 내 코드가 \<link> 태그 한 줄만 있으면 되므로 깔끔해진다.

  => 가독성 증가

- 한 파일로 여러 html 문서에 스타일 적용이 가능해진다.

  => 재사용성 증가

