# CSS Transform & Transition

## `transform` 

`transform` 속성을 사용하여 원하는 요소를 (좌표 공간을) 변형 시킬 수 있다. 대표적인 효과로 이동(translate), 회전(rotate), 크기변경(scale), 기울임(skew)등이 있다.



## `transform-origin`

`transform` 이 적용 될 꼭짓점 (혹은 원점)을 지정할 수 있다. Default 값은 `center` 이다.



## `transition`

`transition` 은 `transform` 등이 CSS 속성을 변화시킬 때 애니메이션 속도를 조절할 수 있도록 돕는다. 속성의 변화가 바로 적용되는 것이 아닌 일정 기간에 걸쳐 일어나도록 한다.

```html
<body>
  <p>아래 박스는 width, height, background-color, transform을 위한 트랜지션을 결합합니다. 박스 위에 마우스를 올려 속성들의 애니메이션을 보세요.</p>
  <div class="box"></div>
</body>

<style>
  .box {
      border-style: solid;
      border-width: 1px;
      display: block;
      width: 100px;
      height: 100px;
      background-color: #0000FF;
      -webkit-transition:width 2s, height 2s, background-color 2s, -webkit-transform 2s;
      transition:width 2s, height 2s, background-color 2s, transform 2s;
  }

  .box:hover {
      background-color: #FFCCCC;
      width:200px;
      height:200px;
      -webkit-transform:rotate(180deg);
      transform:rotate(180deg);
  }
</style>
```



##`transition-timing-function`

지정된 `transition` 속성에서 지정된 애니메이션의 속도를 조절할 수 있다. 크롬 브라우저에서 직접 커브를 만질 수 있다.

[커브 생성과 예시를 그 자리에서 볼 수 있다](https://matthewlein.com/tools/ceaser)

