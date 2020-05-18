### ** 선택자 종류

ㄱ. 태그

ㄴ. 클래스 / 아이디

ㄷ. 자식(children)

​     ex) .div1 i  {    }   => class="div1" 인 것 속에 i 태그인 것들

ㄹ. 직속 자식(direct children)

​    ex) .div1 > i {   }   => class="div1" 인 것 바로 아래 i 태그인 것들

ㅁ. 복수 선택    =>   or 느낌

​    ex) .two, .four {   }

ㅂ. 여러 조건    =>  and 느낌

​    ex) .outside.one {   }

​           .inside.two {   }        => 두 클래스 모두 속하는 경우

ㅅ. 가상 클래스(pseudo-class)

​    ex)  .div1 p:nth-child(3) {   }        => div1의 자식인 p 태그 중 세 번째

​           .div1 p:first-child {   }            => div1의 자식인 p 태그 중 처음

​           .div1 p:last-child {   }             => div1의 자식인 p 태그 중 마지막

​          .div1 p:not(:last-child) {   }    => div1의 자식인 p 태그 중 마지막만 제외

​          .div1 p:not(:first-child) {   }   => div1의 자식인 p 태그 중 처음만 제외



​          h1:hover {   }                          => 마우스가 h1 태그에 올라갔을 때



### ** CSS 상속

- 어떤 태그에 여러 스타일 속성이 적용되어 있을 때,

  하위 태그는 어떻게 적용되는가?

  ***ans : 물려받는 스타일도, 아닌 스타일도 있다. <u>이는 태그 마다 다르다.</u>***



* 웬만하면 물려받는 속성들

![](inherit.jpg)

- ex) a 태그는 color 속성이 상속되지 않는다.

  ​     => 이를 강제로 상속 받으려면 아래와 같이 설정해줘야 한다.

  ```html 
  <style>
      .div a {
  		color: inherit;
      }
  </style>
  ```



### ** 여러 선택자가 같은 요소를 가리키면?

=> 명시도(Specificity)가 높은 선택자, 즉 우선순위가 높은 선택자가 적용된다.



![](specificity.jpg)

