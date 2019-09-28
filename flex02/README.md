# CSS3 Flexible Box

Flex는 요소의 크기가 불분명하거나 동적인 경우에도, 각 요소를 정렬할 수 있는 효율적인 방법을 제공함.



Flex는 Container 와 Items로 나뉨.

Container는 Items를 감싸는 부모 요소이며, 각 Item을 정렬하기 위해선 Container가 필수.



***각각 적용하는 속성이 구분.**

Container : `display`, `flex-flow`, `justify-content`

Items : `order`, `flex`, `align-self`



![Flex](https://heropy.blog/images/screenshot/flex-base.jpg)

<br>

## Flex Container

Flex Container를 위한 속성.

| 속성            | 의미                                                  |
| --------------- | ----------------------------------------------------- |
| display         | Flex Container를 정의                                 |
| flex-flow       | `flex-direction`와 `flex-wrap`의 단축 속성            |
| flex-direction  | Flex Items의 주 축(main-axis)을 설정                  |
| flex-wrap       | Flex Items의 여러 줄 묶음(줄 바꿈) 설정               |
| justify-content | 주 축(main-axis)의 정렬 방법을 설정                   |
| align-content   | 교차 축(cross-axis)의 정렬 방법을 설정(2줄 이상)      |
| align-items     | 교차 축(cross-axis)에서 Items의 정렬 방법을 설정(1줄) |

<br><br>

### display

`display` 속성으로 Flex Container를 정의.

| 값          | 의미                                |
| ----------- | ----------------------------------- |
| flex        | Block 특성의 Flex Container를 정의  |
| inline-flex | Inline 특성의 Flex Container를 정의 |



`display:flex;` 로 지정된 Flex Container는 Block 요소와 같은 성향(수직 쌓임).

`display:inline-flex;` 로 지정된 Flex Container는 Inline(Inline Block) 요소와 같은 성향(수평 쌓임).

***여기서 말하는 수직과 수평 쌓임은 Items가 아니라 Container, 두 값의 차이는 내부에 Items에는 영향을 주지 않음.**

![Flex](https://heropy.blog/images/screenshot/flex-display.jpg)

<br><br>

### flex-flow

이 속성은 단축 속성으로 Flex Items의 주 축(main-axis)을 설정하고 Items의 여러 줄 묶음(줄 바꿈)도 설정.

`flex-flow:주축 줄바꿈;`

EX01)

```css
.flex-container{
    flex-flow:row-reverse wrap;
}
```

| 값             | 의미                               | 기본값   |
| -------------- | ---------------------------------- | -------- |
| flex-direction | Items의 주 축(main-axis)을 설정    | `row`    |
| flex-wrap      | Items의 여러 줄 묶음(줄 바꿈) 설정 | `nowrap` |

<br>

#### flex-direction

Items의 주 축(main-axis)을 설정.

| 값             | 의미                                         | 기본값 |
| -------------- | -------------------------------------------- | ------ |
| row            | Items를 수평축(왼쪽에서 오른쪽으로)으로 표시 | `row`  |
| row-reverse    | Items를 `row`의 반대 축으로 표시             |        |
| column         | Items를 수직축(위에서 아래로)으로 표시       |        |
| column-reverse | Items를 `column`의 반대 축으로 표시          |        |

`flex-direction:주축;`

![Flex](https://heropy.blog/images/screenshot/flex-direction.jpg)

<br>

#### 주 축(main-axis)과 교차 축(cross-axis)

값 `row`는 Items를 수평축으로 표시하므로 이때 주 축이 수평, 교차 축은 수직

반대로 값 `column`은 Items를 수직축으로 표시하므로 주 축은 수직, 교차 축은 수평

***방향(수평,수직)에 따라 주 축과 교차 축이 달라짐.**

![Flex](https://heropy.blog/images/screenshot/flex-direction-main-axis.jpg)

<br>

#### 시작점(flex-start)과 끝점(flex-end)

주 축이나 교차 축의 시작하는 지점과 끝나는 지점을 지칭.

이 역시 방향에 따라 시작점과 끝점이 달라짐.

![Flex](https://heropy.blog/images/screenshot/flex-direction-main-start.jpg)

![Flex](https://heropy.blog/images/screenshot/flex-direction-cross-start.jpg)

<br>

#### flex-wrap

Items의 여러 줄 묶음(줄 바꿈)을 설정.

| 값           | 의미                                           | 기본값   |
| ------------ | ---------------------------------------------- | -------- |
| nowrap       | 모든 Items를 여러 줄로 묶지 않음(한 줄에 표시) | `nowrap` |
| wrap         | Items를 여러 줄로 묶음                         |          |
| wrap-reverse | Items를 `wrap`의 역 방향으로 여러 줄로 묶음    |          |

`flex-wrap:여러줄묶음;`

기본적으로 Items는 한 줄에서만 표시되고 줄 바꿈 되지 않음.

이는 지정된 크기(주 축에 따라 `width` 나 `height`)를 무시하고 한 줄 안에서만 가변.

Items를 줄 바꿈 하려면 값으로 `wrap`을 사용.

![Flex](https://heropy.blog/images/screenshot/flex-wrap.jpg)

<br>

#### justify-content

주 축(main-axis)의 정렬 방법 설정.

| 값            | 의미                                                         | 기본값       |
| ------------- | ------------------------------------------------------------ | ------------ |
| flex-start    | Items를 시작점(flex-start)으로 정렬                          | `flex-start` |
| flex-end      | Items를 끝점(flex-end)으로 정렬                              |              |
| center        | Items를 가운데 정렬                                          |              |
| space-between | 시작 Item은 시작점에, 마지막 Item은 끝점에 정렬되고 나머지 Items는 사이에 고르게 정렬됨 |              |
| space-around  | Items를 균등한 여백을 포함하여 정렬                          |              |

`justify-content:정렬방법;`

![Flex](https://heropy.blog/images/screenshot/flex-justify-content.jpg)

<br>

#### align-content

교차 축(cross-axis)의 정렬 방법 설정.

**`flex-wrap` 속성을 통해 Items가 여러 줄(2줄 이상)이고 여백이 있을 경우만 사용.**

> Items가 한 줄일 경우 align-items 속성을 사용.

| 값            | 의미                                                         | 기본값    |
| ------------- | ------------------------------------------------------------ | --------- |
| stretch       | Container의 교차 축을 채우기 위해 Items를 늘림               | `stretch` |
| flex-start    | Items를 시작점(flex-start)으로 정렬                          |           |
| flex-end      | Items를 끝점(flex-end)으로 정렬                              |           |
| center        | Items를 가운데 정렬                                          |           |
| space-between | 시작 Item은 시작점에, 마지막 Item은 끝점에 정렬되고 나머지 Items는 사이에 고르게 정렬됨 |           |
| space-around  | Items를 균등한 여백을 포함하여 정렬                          |           |

`align-content:정렬방법;`

값 `stretch`는 교차 축에 해당하는 너비(속성 `width` or `height`)가 값이 `auto`(기본값)일 경우 교차 축을 채우기 위해 자동으로 늘어남.

![Flex](https://heropy.blog/images/screenshot/flex-align-content.jpg)

<br>

#### align-items

교차 축(cross-axis)에서 Items의 정렬 방법을 설정.

Items가 한 줄일 경우 많이 사용.

**Items가 `flex-wrap`을 통해 여러 줄(2줄 이상)일 경우 `align-content` 속성이 우선.**

**`align-items`를 사용하려면 `align-content` 속성을 기본값(`stretch`)으로 설정해야 함.**

| 값         | 의미                                           | 기본값    |
| ---------- | ---------------------------------------------- | --------- |
| stretch    | Container의 교차 축을 채우기 위해 Items를 늘림 | `stretch` |
| flex-start | Items를 각 줄의 시작점(flex-start)으로 정렬    |           |
| flex-end   | Items를 각 줄의 끝점(flex-end)으로 정렬        |           |
| center     | Items를 가운데 정렬                            |           |
| baseline   | Items를 문자 기준선에 정렬                     |           |

`align-items:정렬방법;`

![Flex](https://heropy.blog/images/screenshot/flex-align-items.jpg)

<br><br>

## Flex Items

Flex Items를 위한 속성.

| 속성        | 의미                                                 |
| ----------- | ---------------------------------------------------- |
| order       | Flex Item의 순서를 설정                              |
| flex        | `flex-grow`, `flex-shrink`, `flex-basis`의 단축 속성 |
| flex-grow   | Flex Item의 증가 너비 비율을 설정                    |
| flex-shrink | Flex Item의 감소 너비 비율을 설정                    |
| flex-basis  | Flex Item의 (공간 배분 전) 기본 너비 설정            |
| align-self  | 교차 축(cross-axis)에서 Item의 정렬 방법을 설정      |

<br><br>

### order

Item의 순서를 설정.

Item에 숫자를 지정하고 숫자가 클수록 순서가 밀림.

음수 허용.

> HTML 구조와 상관없이 순서를 변경할 수 있기 때문에 유용.

| 값   | 의미               | 기본값 |
| ---- | ------------------ | ------ |
| 숫자 | Item의 순서를 설정 | `0`    |

`order:순서;`

![Flex](https://heropy.blog/images/screenshot/flex-order.jpg)

<br><br>

### flex

Item의 너비(증가, 감소, 기본)를 설정하는 단축 속성.

| 값          | 의미                                 | 기본값 |
| ----------- | ------------------------------------ | ------ |
| flex-grow   | Item의 증가 너비 비율을 설정         | `0`    |
| flex-shrink | Item의 감소 너비 비율을 설정         | `1`    |
| flex-basis  | Item의 (공간 배분 전) 기본 너비 설정 | `auto` |

`flex:증가너비 감소너비 기본너비;`

```css
.item{
    flex:1 1 20px; /* 증가너비 감소너비 기본너비 */
    flex:1 1; /* 증가너비 감소너비 */
    flex:1 20px; /* 증가너비 기본너비(단위를 사용하면 flex-basis가 적용됨) */
}
```



`flex-grow`를 제외한 개별 속성은 생략 가능, `flex:1;`로 작성하면 `flex-grow:1;`과 같음.

**flex-basis의 기본값은 auto이지만 단축 속성인 flex에서 그 값을 생략할 경우 0이 적용.**

`flex:1;` == `flex:1 1;` !=  `flex:1 1 auto;`

`flex:1;` == `flex:1 1;` ==  `flex:1 1 0;`

<br>

#### flex-grow

Item의 증가 너비 비율을 설정.

숫자가 크면 더 많은 너비를 가짐.

Item이 가변 너비가 아니거나, 값이 `0`일 경우 효과가 없음.

| 값   | 의미                         | 기본값 |
| ---- | ---------------------------- | ------ |
| 숫자 | Item의 증가 너비 비율을 설정 | `0`    |

`flex-grow:증가너비;`

모든 Items의 총 증가 너비(flex-grow)에서 각 Item의 증가 너비의 비율 만큼 너비를 가질 수 있음.

EX)

Item이 3개이고 증가 너비가 각각 `1`, `2`, `1` 이면,

첫 번째 Item은 총 너비의 25%(1/4),

두 번째 Item은 총 너비의 50%(2/4),

세 번째 Item은 총 너비의 25%(1/4)

![Flex](https://heropy.blog/images/screenshot/flex-grow.jpg)

<iframe width="100%" height="300" src="//jsfiddle.net/Choilee/w2ne01t3/embedded/js,html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

[https://jsfiddle.net/Choilee/w2ne01t3/](https://jsfiddle.net/Choilee/w2ne01t3/)

<br>

#### flex-shrink

Item이 감소하는 너비의 비율을 설정.

숫자가 크면 더 많은 너비가 감소.

Item이 가변 너비가 아니거나, 값이 `0`일 경우 효과 없음.

| 값   | 의미                         | 기본값 |
| ---- | ---------------------------- | ------ |
| 숫자 | Item의 감소 너비 비율을 설정 | `1`    |

`flex-shrink:감소너비;`

감소 너비(`flex-shrink`)는  `width`, `height`, `flex-basis` 등으로 요소의 너비가 지정된 경우 요소의 너비에 영향을 받기 때문에 계산하기 까다로움.

Container의 너비가 줄어 Items의 너비에 영향을 미칠 경우, 영향을 미치기 시작한 지점부터 줄어든 거리 만큼 감소 너비 비율에 맞게 Item의 너비가 줄어듬. 



EX01) - 너비 지정 X

Container의 너비가 줄어 Item의 너비에 영향을 미치기 시작한 지점부터 실제 줄어든 거리가 `90px`일 때,

요소 너비가 같은 Item이 2개이고 지정된 감소 너비가 각각 2와 1이라면, 감소 너비는 2:1 비율.

첫 번째 Item은 `90px`의 2/3인 `60px` 만큼 너비가 감소,

두 번째 Item은 `90px`의 1/3인 `30px` 만큼 너비가 감소.



EX02) - 너비 지정 O

Container의 너비가 줄어 Item의 너비에 영향을 미치기 시작한 지점부터 실제 줄어든 거리가 `90px`일 때,

요소 너비가 같은 Item이 2개이고 요소 너비는 각각 `200`과 `100`이고,

지정된 감소 너비가 각각 `2`와 `1`이라면, `200 x 2 = 400`과 `100 x 1 = 100` 감소 너비는 4:1 비율.

첫 번째 Item은 `90px`의 4/5인 `72px` 만큼 너비가 감소,

두 번째 Item은 `90px`의 1/5인 `18px` 만큼 너비가 감소.

![Flex](https://heropy.blog/images/screenshot/flex-shrink.jpg)

<iframe width="100%" height="300" src="//jsfiddle.net/Choilee/p6t4cmya/embedded/js,html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

[https://jsfiddle.net/Choilee/p6t4cmya/](https://jsfiddle.net/Choilee/p6t4cmya/)

<br>

> 계산이 까다로워 활용도는 조금 떨어짐.
>
> 원리 정도만 이해 하자.

<br>

#### flex-basis

Item의 (공간 배분 전) 기본 너비를 설정.

값이 `auto`일 경우 `width`, `height`등의 속성으로 Item의 너비를 설정할 수 있음.

하지만, 단위 값이 주어질 경우 설정할 수 없음.

| 값   | 의미                      | 기본값 |
| ---- | ------------------------- | ------ |
| auto | 가변 Item과 같은 너비     | `auto` |
| 단위 | px, em, cm 등 단위로 지정 |        |

`flex-basis:기본너비;`

![Flex](https://heropy.blog/images/screenshot/flex-basis.jpg)

<br><br>

### align-self

교차 축(cross-axis)에서 개별 Item의 정렬 방법을 설정.

`align-items`는 Container 내 모든 Items의 정렬 방법을 설정.

필요에 의해 일부 Item만 정렬 방법을 변경하려고 할 경우 `align-self`를 사용할 수 있음.

***이 속성은 `align-items` 속성보다 우선.**

| 값         | 의미                                          | 기본값 |
| ---------- | --------------------------------------------- | ------ |
| auto       | Container의 `align-items` 속성을 상속받음     | `auto` |
| stretch    | Container의 교차 축을 채우기 위해 Item을 늘림 |        |
| flex-start | Item을 각 줄의 시작점(flex-start)으로 정렬    |        |
| flex-end   | Item을 각 줄의 끝점(flex-end)으로 정렬        |        |
| center     | Item을 가운데 정렬                            |        |
| baseline   | Item을 문자 기준선에 정렬                     |        |

`align-self:정렬방법;`

![Flex](https://heropy.blog/images/screenshot/flex-align-self.jpg)



