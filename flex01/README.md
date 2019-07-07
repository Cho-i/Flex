# Flex(Flexbox)

## Layout

대부분 사이트는 전체 레이아웃이 수직 구성이며 'Up - Down'로 스크롤 하여 사용.

레이아웃[^1]을 구성할 때 가장 많이 사용하는 요소(Elements)들이 기본적으로 블록(Block) 개념으로 표시(Display)되며 이는 뷰(View)에 수직('Up - Down')으로 쌓이기 때문에 수직 구성은 상대적으로 쉽게 만들 수 있음.

하지만 수평('Left - Right') 구성의 경우는 상황이 좀 다름.

수평 구조를 만드는 속성이 명확하지 않았기 때문, 그래서 많은 경우

`table` `float` `inline-block` `display-cell` 등의 도움을 받음.

<br>

**table(표)**

격자모양 ,그리드모양으로 생긴걸 착안해서 표에 해당하는 table태그로 레이아웃을 잡음 .

<u>문제</u>

표는 구조화된 정보를 또 많은 정보를 잘 정리 정돈하기 위한 정보로서의 의미를 가지고 있는데, 그것을 의미가 없는 레이아웃을 사용하게 되니까 검색 엔진이나 스크린 리더나 여러 html을 해석하는 소프트웨어들의 입장에서는 테이블을 만났을 때 그 테이블이 표로 사용된 것인지 레이아웃으로 사용된 것인지를 구분하기 굉장히 어려웠음.

또 테이블이 아주 복잡하고 코드 양이 많기 때문에, 웹페이지 안에서 테이블이 꽉 차게 되면 짜는 것은 쉽지만 나중에 변경하는 것은 대단히 까다로움.

<br>

**float**

floating 효과는 이미지를 삽화 같은 것으로 표현할때 이미지가 있으면 이미지 옆에 글씨가 흘러가게하는 것.

<br>

EX01

```html
<div class="box"></div>
<div class="box"></div>
<div class="box"></div>
<div class="clear"></div>
```

```css
.box{float:left}
.clear{clear:both}
```

`box`를 제외한 `clear` 라는 다음 요소도 있어야 하기에 실제 사용엔 매우 불편하며, 명확하지 않은 방법.

<br>

EX02

```html
<div class="clear">
    <div class="box"></div>
	<div class="box"></div>
	<div class="box"></div>
</div>
```

```css
.clear::after{content:'';display:block;clear:both}
.box{float:left}
```

수평이 될 요소들에 직접 `float`를 적용하고 그 요소들의 부모(Container)에 미리 설정한 `clear`를 적용.

<u>이 방법은 IE 핵이나 기타 방식을 제외하고 가장 원리에 충실한 방법.</u>

<br>

**<u>이런 방법들을 이용해 레이아웃을 잡는데 많이 사용하지만, 다양한 문제[^2]를 가지고 있기에 수평 레이아웃 구성의 차선책일 뿐 레이아웃을 만들기 위해서 고안된 것이라고 보기 어려움.</u>**



[^1]: 어떤 컨텐츠를 만들 때 그 컨텐츠를 잘 정리 정돈해서 구조화시킬 때 사용하는것
[^2]: Clear, White space 등... (해결은 가능하지만)

<br>

<br>

## Flexbox

Flex는 요소의 크기가 불분명하거나 동적인 경우에도, 각 요소를 정렬할 수 있는 효율적인 방법을 제공.

<br>

> flex는 주로 레이아웃을 잡을 때 사용하며, 여러가지 flex와 관련된 속성들이 다양하게 존재하여 다 아는 것도 쉽지 않음, 또 그것들이 결합됐을 때 어떤 이펙트가 일어날지 파악하는 것도 쉽지 않음....

<br>

### Browser compatibility

https://caniuse.com/#search=flex

<br>

**Chrom**

chrom21 버전부터 display:-webkit-flex를 지원

chrom29 버전부터 display:flex를 지원

<br>

**Firefox**

firefox28 버전부터 display:flex를 지원

<br>

**Microsoft Edge** 

display:flex를 지원

<br>

**Internet Explorer**

https://docs.microsoft.com/en-us/previous-versions/windows/internet-explorer/ie-developer/compatibility/dn265027(v=vs.85)

IE10 버전에서 display:-ms-flexbox를 지원

IE11 버전부터 display:flex를 지원

<br>

**Property**

| Instead of(IE10)           | Use(IE11)       |
| -------------------------- | --------------- |
| -ms-flex-wrap              | flex-wrap       |
| -ms-flex-order, flex-order | order           |
| -ms-flex-pack              | justify-content |
| -ms-flex-align             | align-items     |
| -ms-flex-item-align        | align-self      |
| -ms-flex-line-pack         | align-content   |

<br>

**Value**

| Property                                                | Old value(IE10)    | New value(IE11) |
| ------------------------------------------------------- | ------------------ | --------------- |
| display                                                 | -ms-flexbox        | flex            |
| display                                                 | -ms-inline-flexbox | inline-flex     |
| flex-wrap                                               | none               | nowrap          |
| align-content, align-items, align-self, justify-content | start              | flex-start      |
| align-content, align-items, align-self, justify-content | end                | flex-end        |

<br>

### Container, Items

Flex를 사용하기 위해서는 태그가 두 단계가 필요함.

마치 li태그는 반드시 ul이나 ol 같은 부모 태그가 필요하듯이 정렬하고자 하는 그 각각의 아이템들은 부모에 해당되는 컨테이너가 필요함.

```html
<container>
	<item></item>
    <item></item>
</container>
```

- Flex container : display: flex를 설정 한 부모 엘리먼트

- Flex items : Flex container 내의 자식 엘리먼트

<br>

container와 items에 적용하는 속성이 구분되어 있음.

이걸 구분하여 어떤 속성은 container에게 주고 어떤 것은 item에게 주는 방식으로 코딩해야함.

<br>

|    container    |    item     |
| :-------------: | :---------: |
|     display     |    order    |
|    flex-flow    |    flex     |
| flex-direction  |  flex-grow  |
|    flex-wrap    | flex-shrink |
| justify-content | flex-basis  |
|  align-content  | align-self  |
|   align-items   |             |

