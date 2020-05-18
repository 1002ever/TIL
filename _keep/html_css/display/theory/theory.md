### ** Display



- inline display

  ex) \<span\>, \<b\>, \<i\>

  ㄱ. 다른 요소들과 같은 줄에 머무르려고 하는 성향

  ㄴ. 가로 길이는 필요한 만큼만 차지하는 성향



- block display

  ex) \<div\>, \<h1\>, \<p\>

  ㄱ. 새로운 줄에 가려고 하는 성향

  ㄴ. 가로 길이를 최대한 많이 차지하려고 하는 성향



=> 각 태그 마다 고유의 display 속성 값을 지닌다.

​      이를 변경해주는 속성이 display



ex) 블록 요소인 div를 inline 요소로 변경

```html
<style>
    div {
        display: inline;
    }
</style>
```



> Tip. img 태그는 inline-block 속성 값을 가지므로,

> ​       inline 처럼 줄 바꿈이 없지만, width, height로 박스 공간 설정이 가능하다.

> ​       => 그런데 개발자도구를 통해 보면 inline 요소라고 나와있음..

> ​             하지만 inline-block 특징을 갖고, 증거로 vertical-align 속성 적용이 가능

> ​                                                                    ==> inline 텍스트의 특징도 갖고 있다는 것

> ​       => <u>img 를 div class="container"로 묶고, text-align: center; 를 주면 가운데 정렬.</u>

> ​            <u>단, 이미지를 정렬하는 데 위 방식은 약간 어색함.</u>

> ​            <u>img 태그를 block 요소로 바꿔, margin: 0 auto; 처리해주는 것이 보다 이해하기 좋다.</u>





### *** 다양한 링크

- a 태그 속에 텍스트만 넣을 수 있는 것이 아니다.

  => 이미지로도 링크를 지정할 수 있다.

  ex)

  ```html
  <a href="https://google.com/" target="_blank">
  	<img src="images/google.png" width="200"
  </a>
  ```

  => a 태그에 클래스를 설정하여, display: block; 을 설정해주면 여러 요소를 담은

  ​     박스 형태를 링크로 설정할 수도 있다.



#### ** baseline ?

- 텍스트 밑에 지정된 선

  => 텍스트는 baseline 바로 위에 적힌다.

  ​     margin 기준이 아닌 텍스트 바로 아래에 존재한다.

  ![](baseline.jpg)



- 이미지의 경우도 바로 아래가 baseline

![](baseline2.jpg)



- inline-block 의 경우, 바로 직전 요소의 baseline이 baseline으로 설정된다.

​      ex) alex와 chris의 baseline이 같은 것을 볼 수 있음

![](baseline3.jpg)

​	*** 단, inline-block 속에 텍스트 요소가 없다면(= 줄이 없다면), baseline은 그냥 box 영역 바로 밑에 설정

​     ex)

![](baseline4.jpg)



​    \*\*\* <u>***또 overflow 설정 시, baseline은 유동적일 수 있다.***</u>



