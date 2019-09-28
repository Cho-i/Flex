# Flexbox로 만들 수 있는 레이아웃

1. ## 스크롤 없는 100% 레이아웃

   ![그림](https://d2.naver.com/content/images/2018/12/helloworld-201811-flex_04.png)

   **콘텐츠의 길이에 상관없이 브라우저 화면 전체를 채우는 레이아웃.**

   <br>

   웹 페이지 위에 있는 메뉴 영역의 높이는 고정.

   부모 영역에서 메뉴 영역을 뺀 나머지 영역 전체를 자식 요소가 채움.

   콘텐츠의 길이가 길어지면스크롤 막대가 브라우저가 아니라 콘텐츠 영역에 나타남.

   <iframe width="100%" height="300" src="//jsfiddle.net/Choilee/5tn9zudp/embedded/html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

   [https://jsfiddle.net/Choilee/5tn9zudp/](https://jsfiddle.net/Choilee/5tn9zudp/)

   <br>

   container에 `flex-direction:column;` 속성을 적용해 item을 수직으로 정렬.

   item에는 `flex:1;` 속성을 적용해 item이 빈 공간을 채우게 함.

   <br><br>

2. ## 내비게이션 영역

   ![그림](https://d2.naver.com/content/images/2018/12/helloworld-201811-flex_12.png)

   <br>

   메뉴의 대부분을 내비게이션 영역의 왼쪽으로 정렬하고, 1 ~ 2 개의 메뉴만 오른쪽으로 정렬.

   주로 GNB(Global Navigation Bar)에 해당하는 요소나 로그인 버튼을 오른쪽으로 정렬.

   <iframe width="100%" height="300" src="//jsfiddle.net/Choilee/w03sgzh2/embedded/html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

   [https://jsfiddle.net/Choilee/w03sgzh2/](https://jsfiddle.net/Choilee/w03sgzh2/)

   <br>

   크기가 고정되어야 하는 item에는 `flex:none;` (`flex:0 0 auto;`)속성을 적용.

   오른쪽으로 정렬할 GNB나 로그인 버튼에 해당하는 요소에는 `margin-left:auto;`.

   <br>

   ### **`flex:none;` 속성으로 자식 요소의 크기 고정**

   `flex:none;`은 `flex-grow:0;` 속성, `flex-shrink:0;` 속성, `flex-basis:auto;` 속성을 축약해 표현한 것.

   ### **`margin-left:auto;` 속성으로 자식 요소를 오른쪽에 배치**

   요소의 바깥 여백(margin)을 설정하는 속성에 속성값으로 auto를 적용하면 flexbox에서 item을 쉽게 배치할 수 있음.

   `margin:auto;` 속성을 적용하면 item의 바깥 여백이 자동으로 확장되어 item이 container의 가운데에 위치.

   item을 수평으로 배치할 때 'auto'속성값을 사용할 수 있음.

   - `margin-right:auto;` - 바깥 여백이 오른쪽의 모든 공간을 차지하기 위해 item을 오른쪽에서 왼쪽으로 밈.

   - `margin:0 auto;` - 바깥 여백이 item을 양쪽에서 밀기 때문에 item이 수평 중앙에 위치함.

   - `margin-left:auto;` - 바깥 여백이 왼쪽의 모든 공간을 차지하기 위해 item을 왼쪽에서 오른쪽으로 밈.

   ![그림](https://d2.naver.com/content/images/2018/12/helloworld-201811-flex_14.png)

   item을 수직으로 배치할 때 'auto'속성값을 사용할 수 있음.

   - `margin-bottom:auto;` - 바깥 여백이 아래쪽의 모든 공간을 차지하기 위해 item을 아래쪽에서 위쪽으로 밈.

   - `margin:auto 0;` - 바깥 여백이 item을 위아래로 밀기 때문에 item이 수직 중앙에 위치.

   - `margin-top:auto;` - 바깥 여백이 위쪽의 모든 공간을 차지하기 위해 item을 위쪽에서 아래쪽으로 밈.

     ![그림](https://d2.naver.com/content/images/2018/12/helloworld-201811-flex_15.png)

   > flexbox에서 `margin:auto;` 속성으로 레이아웃을 구현하는 방법이 hack이라고 생각하거나 버그를 일으키는 요인이 될 수도 있지만, 이 속성은 오히려 flexbox 명세에서 권장하는 방법임.

   <br>

   <br>

3. ## 브라우저 화면 아래 붙는 푸터

   ![그림](https://d2.naver.com/content/images/2018/12/helloworld-201811-flex_16.png)

   <br>footer는 보통 브라우저 화면의맨 아래에 위치, 콘텐츠의 길이가 화면보다 짧으면 푸터는 콘텐츠가 짧아진 만큼 위로 올라간 위치에 표시됨.

   flexbox를 사용하면 콘텐츠의 길이와 상관없이 항상 화면 아래에 표시되는 푸터를 만들 수 있음.

   <iframe width="100%" height="300" src="//jsfiddle.net/Choilee/Lwe9rzvo/embedded/html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

   [https://jsfiddle.net/Choilee/Lwe9rzvo/](https://jsfiddle.net/Choilee/Lwe9rzvo/)

   <br><br>

4. ## 정렬이 다른 메뉴

   ![그림](https://d2.naver.com/content/images/2018/12/helloworld-201811-flex_18.png)

   <br>

   ```css
   .flex-container{
       display:flex;
       justify-content:space-between;
   }
   ```

   <br><br>

5. ## 폼 레이블 수직 중앙 정렬

   ![그림](https://d2.naver.com/content/images/2018/12/helloworld-201811-flex_20.png)

   <br>

   폼 요소의 레이블을 수직 중앙에 정렬하는 레이아웃.

   한 줄짜리 텍스트뿐만 아니라 두 줄 이상의 텍스트도 수직 중앙에 정렬.

   <iframe width="100%" height="300" src="//jsfiddle.net/Choilee/tkeqfwbj/embedded/html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

   [https://jsfiddle.net/Choilee/tkeqfwbj/](https://jsfiddle.net/Choilee/tkeqfwbj/)

   <br><br>

6. ## 중앙 정렬 아이콘

   ![그림](https://d2.naver.com/content/images/2018/12/helloworld-201811-flex_22.png)

   <br>

   자식 요소인 아이콘이 부모 요소의 정중앙에 위치하는 레이아웃.

   ![그림](https://d2.naver.com/content/images/2018/12/helloworld-201811-flex_23.png)

   1. container에 `align-items:center;` 속성과 `justify-content:center;`속성을 적용.

      ```css
      .flex-container{
          display:flex;
          align-items:center;
          justify-content:center;
      }
      ```

      

   2. item에 `margin:auto;` 속성을 적용.

      ```css
      .flex-container{
          display:flex;
      }
      .flex-item{
          margin:auto;
      }
      ```

      <br><br>

7. ## 유동 너비 박스

   ![그림](https://d2.naver.com/content/images/2018/12/helloworld-201811-flex_24.png)

   **container인 부모 요소 크기에 따라 item인 자식 요소의 크기가 콘텐츠의 크기보다 줄어드는 레이아웃.**

   <br>

   부모 요소의 크기가 크다면 자식 요소의 크기는 콘텐츠 너비를 모두 수용할 수 있을 만큼 크지만, 부모 요소의 크기가 줄어들어 콘텐츠의 크기보다 작아지면 자식 요소의 크기가 콘텐츠의 크기보다 줄어듬.

   <iframe width="100%" height="300" src="//jsfiddle.net/Choilee/3kzpj4fo/embedded/html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

   [https://jsfiddle.net/Choilee/3kzpj4fo/](https://jsfiddle.net/Choilee/3kzpj4fo/)

   <br>

   item에 `max-width:300px;` ,`flex:0 1 auto;` flex속성 기본값.

   container 크기가 커질땐 item 크기는 변하지 않지만 작아지면 item의 크기가 작아짐.

   <br>

   <br>

8. ## 말줄임과 아이콘

   ![그림](https://d2.naver.com/content/images/2018/12/helloworld-201811-flex_27.png)

   <br>

   container인 부모 요소의 크기가 작아 item인 자식 요소의 텍스트를 모두 표시할 수 없을 때 줄임표(...)가 나타나게 하는 레이아웃.

   이 때 텍스트 영역 옆에 있는 아이콘의 크기는 고정.

   <iframe width="100%" height="300" src="//jsfiddle.net/Choilee/1k0wthc9/embedded/html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

   [https://jsfiddle.net/Choilee/1k0wthc9/](https://jsfiddle.net/Choilee/1k0wthc9/)

   <br>

   container에 `display:inline-flex;` `max-width:100%;` 속성 적용.

   <br><br>

9. ## 위아래로 흐르는 목록

   ![그림](https://d2.naver.com/content/images/2018/12/helloworld-201811-flex_29.png)

   **자식 요소를 위아래로 먼저 정렬하고 자식 요소가 부모 요소를 벗어나면 줄을 바꿔 다시 위아래로 정렬하는 레이아웃.**

   <br>

   ```css
   .flex-container{
       display:flex;
       flex-flow:column wrap;
       justify-content:space-around;
       align-content:space-around;
   }
   ```

   <br><br>

10. ## 가로세로 비율을 유지하는 반응형 박스

    ![그림](https://d2.naver.com/content/images/2018/12/helloworld-201811-flex_34.png)

    **브라우저의 크기에 따라 박스의 가로세로 크기가 동일한 비율로 늘어나거나 줄어드는 반응형 레이아웃.**

    <br>

    <iframe width="100%" height="300" src="//jsfiddle.net/Choilee/ho4xrg0w/embedded/html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

    [https://jsfiddle.net/Choilee/ho4xrg0w/](https://jsfiddle.net/Choilee/ho4xrg0w/)

    <br>

    ```css
    .flex-container{
        display:flex;
        flex-wrap:wrap;
    }
    .flex-item{
        flex-basis:33.3%;
        display:flex;
        flex-direction:column;
    }
    .flex-item-image{
        flex:auto;
        /* flex-grow:1;flex-shrink:1;flex-basis:auto; */
    }
    ```

    item이 일정한 비율로 유지되게 `flex-basis:33.3%;` 속성을 적용.

    이미지 박스는 `flex:auto;` (`flex:1 1 auto;`)속성을 적용.

    <br>