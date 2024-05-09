이미지 가운데 정렬하는 방법
```html
display:block; // div,p, h 등은 block 속성을 이미 갖고 있어서 생략 가능
margin-left: auto; 
margin-right: auto;
```

**vw** : 현재 창 크기에 비례한 크기
**%** : 부모 사이즈에 비례한 크기

자주 사용하는 글자 스타일들
```html
font-size : 20px; 
font-family : 'gulim'; 
color : black; 
letter-spacing : -1px; 
text-align : center; 
font-weight : 600;
```

`<span>` : 글자를 감쌀 수 있는 별 뜻 없는 태그

style은 클래스로 선언하고,
id는 javascript를 위해 사용한다.

**스타일 겹칠 때 우선순위** : 태그에 style > id > class > tag

**display: block** : 가로 행을 전부 차지하게 해주셈

> [!NOTE]
> 레이아웃 전체를 감싸는 박스를 만들어두면 유용하다. 
> class="container"인 박스 하나로 감싸고 시작하자. 
> 이를 wrapper 박스, container 박스라고 한다.

**width: 100%;** : 부모 태그 width의 100%를 의미

**div 가로로 정렬하는 방법**
``` css
float: left; // 왼쪽으로 정렬해주셈. 
// 기본 레이아웃 흐름에서 벗어나 요소의 모서리가 페이지의 왼쪽이나 오른쪽으로 이동함.
float : none; clear: both;  // float 다음에 오는 요소에 주면 float로 발생하는 버그 해결
```

```html
display: inline-block; 스타일에 주고

<div class="a"></div><div class="b"></div> 줄바꿈 없이 태그 작성하면 잘 정렬됨

<div class="a"></div><!--
--><div class="b"></div> 중간에 주석 넣고 엔터키 쳐도 되긴 함
```
**display: inline-block** : 내 크기만큼 차지하게 해주셈