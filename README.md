# home-work

## mission_01

### 마크업 구조
- - -

#### 기본 구조


상품들을 &lt;ul&gt;태그를 사용하여 목록으로 만들었습니다.

```html
<h1 class="sr_only">상품 목록</h1>
<h2 class="sr_only">상품</h2>
<ul class="product_list reset_list">
  <li>상품1</li>
  <li>상품2</li>
  <li>상품3</li>
</ul>
``` 
sr_only 클래스를 사용하여 주 제목과 부 제목은 숨김 처리를 했습니다. 

reset_list 클래스를 사용하여 list의 불필요한 요소들을 제거했습니다.

큰 이미지를 사용하는 상품과 작은 이미지를 사용하는 상품의 위치를 정리해주기 위해서 product_list 클래스를 사용했습니다.

```css
.product_list{
  width: var(--big_box_width);
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-between;
}
```
&lt;ul&gt; 태그의 너비값을 큰 이미지의 상품과 동일하게 설정해주고 flex를 사용하여 가로방향으로 정렬하되 설정해놓은 너비값을 벗어나지 않게해서 상품들을 정렬했습니다.

새로운 상품들이 추가 되었을때 아래에 계속해서 위치가 정렬되게 하기위해 사용했습니다.

- - -

#### 큰 이미지 상품 (big_box)

```html
<li class="product">
  <a href="/" class="go_buy big_box">
    <div class="product_info">
      <div class="big_logo">
        <img src="img/logo1.png" alt="오뚜기 로고" class="big_logo_fit"/>
      </div>
      <span class="big_description">따뜻한 차 향기</span>
    </div>
    <div class="product_image">
      <img src="img/product1.jpg" alt="오뚜기 꿀 생강차" class="big_product_image" />
    </div>
    <button class="buy_button">&gt;</button>
  </a>
</li>
```

큰 이미지 상품 정보를 담고 있는 부분을 하나의 커다란 anchor로 사용했습니다.

go_buy 클래스는 anchor 태그가 호버시 동작할 내용을 담고 있습니다.

- - -

**big_box 클래스를 설명하겠습니다.**

```css
.big_box{
  border: 1px solid #C4C4C4;
  position: relative;
  box-sizing: border-box;
  width: var(--big_box_width);
  height: var(--big_box_height);
  padding: 20px 28px; 
  margin: 10px 0;

  display: flex;
  flex: left;
}
```
상품의 정보 요소들(로고, 설명, 이미지)이 항상 동일한 사이즈를 가져야 한다고 생각했습니다.

버튼의 위치를 고정해주기 위해 position을 relative로 설정했습니다.

큰 상자의 요소들은 [로고와 설명]이 [이미지]와 가로로 배치되어 있기 때문에 두 부분으로 묶어서
flex를 사용해서 배치해주었습니다. 

- - -
#### 클래스 설명


|클래스           |                            설명|
|----------------|--------------------------------|
|big_logo         | 큰 상품 로고가 들어갈 위치를 지정|
|big_logo_fit     | 로고 이미지의 크기에 상관없이 지정된 위치에 로고를 넣어줌|
|big_description  | 큰 상품 설명 글이 들어갈 위치를 지정, 너비 값은 고정 높이는 최소값만 지정|
|product_image    | 내용없음 |
|big_product_image| 큰 상품 이미지의 크기에 상관없이 크기 고정|

#### 작은 이미지 상품 (small_box)

```html
<li class="product">
  <a href="/" class="go_buy small_box">
    <div class="small_logo">
      <img src="img/logo2.png" alt="Kamill 로고" class="small_logo_fit">
    </div>
    <span class="small_description">핸드크림 모음</span>
    <img src="img/product2.jpg" alt="Kamill 핸드크림" class="small_product_image">
    <button class="buy_button">&gt;</button>
  </a>
</li>
```
작은 상품의 경우에도 큰 상품과 같이 anchor로 지정했습니다.

- - -

**small_box 클래스를 설명하겠습니다.**

```css
.small_box{
  position: relative;  
  box-sizing: border-box;
  border: 1px solid #C4C4C4;
  padding-left: 23px;
  padding-right: 24.99px;
  padding-block: 14px;
  margin: 10px 0;
  width: var(--small_box_width);
  height: var(--small_box_height);
  
  display: flex;
  flex-flow: column;
}
```

작은 상자도 큰 상자와 같이 항상 동일한 사이즈를 가지기 위해 상자를 크기를 지정했습니다.

내부의 요소들이 세로로 나열되어 있기 때문에 felx를 사용해 세로로 정렬했습니다.

|클래스           |                            설명|
|----------------|--------------------------------|
|small_logo         | 작은 상품 로고가 들어갈 위치를 지정|
|small_logo_fit     | 로고 이미지의 크기에 상관없이 지정된 위치에 로고를 넣어줌|
|small_description  | 작은 상품 설명 글이 들어갈 위치를 지정, 너비 값은 고정 높이는 최소값만 지정|
|small_product_image| 작은 상품 이미지의 크기에 상관없이 크기 고정|

- - -
---

#### 구매하기 구현

```css
.buy_button{
  border: 0 solid black;
  color: white;
  background: var(--button_color);
  position: absolute;
  bottom: 20px;
  left: 20px;
  width: var(--button_size_width);
  height: var(--button_size_height);  
}
```
버튼의 위치는 기존의 box들의 position을 relative했기 때문에, position을 사용해 위치를 고정했습니다.

```css
.go_buy:hover > .buy_button{
  background: #0074E9;
  width: var(--button_hover_width);
  height: var(--button_hover_height);
}

.go_buy:hover > .buy_button::before{
  content: "구매하기 ";
  color: white;
  font-family: var(--small_font_family);
}

.big_box:hover,
.small_box:hover{
  border-color:#0074E9;
}
```
기존의 상품들을 &lt;a&gt; 태그로 묶고 go_buy 클래스를 지정했었습니다.

go_buy 클래스를 사용해서 마우스가 호버 시, 버튼이 변하고 상자의 색이 변하게 했습니다.

- - -

#### css 변수 

상품의 개수가 늘어났을 때, 유지보수에 용이할 수 있도록 필요하다고 생각한 수치들을 변수로 지정했습니다.

```css
:root{
  /* 큰 박스 정보 */
  --big_box_width: 502px;
  --big_box_height: 310px;
  /* 큰 이미지 상품 정보 */
  --big_product_log_width: 112px;
  --big_product_log_height: 67px;
  --big_product_name_width: 200px;
  --big_product_name_height: 37px;
  --big_product_width: 222px;
  --big_product_height: 270px;
  /* 큰 이미지 상품 폰트 */
  --big_font_family: "Noto Sans", sans-serif;
  --big_font_color: #4E4E4E;
  --big_font_size: 24px;
  --big_font_style: normal;
  --big_font_weight: 700;
  --big_font_line_height: 150%;
  /* 작은 박스 정보 */
  --small_box_width: 243px;
  --small_box_height: 310px;
  /* 작은 이미지 상품 정보 */
  --small_product_log_width: 114px;
  --small_product_log_height: 42px;
  --small_product_name_width: 200px;
  --small_product_name_height: 27px;
  --small_product_width: 195px;
  --small_product_height:196px;
  /* 작은 이미지 상품 폰트 */
  --small_font_family: "Noto Sans", sans-serif;
  --small_font_color: #555;
  --small_font_size: 18px;
  --small_font_style: normal;
  --small_font_weight: 700;
  --small_font_line_height: 150%;
  /* 버튼 정보 */
  --button_size_width: 42px;
  --button_size_height: 42px;
  --button_color: #C4C4C4;
  --button_hover_width: 112px;
  --button_hover_height: 42px;
}
```
