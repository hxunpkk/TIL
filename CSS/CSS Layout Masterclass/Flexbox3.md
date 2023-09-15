## flex-wrap

```
기본적으로 flexbox 는 flex 컨테이너 안의 항목들을
한 줄로 표시하려고 한다

아래 예시를 한번 확인해보자.
```

<br>

```
.box {
  width: 200px;
  height: 200px;
}
```

해당 박스가 각각 10개와 6개일때를 비교해 보자.

![flow1](../../img/CSS/flow1.JPG)

![flow2](../../img/CSS/flow2.JPG)

기본적으로 flexbox 는 컨테이너 안의 항목을 한줄로 표시하고

이에 따라 설정한 너비 속성이 무시되는 모습을 볼 수 있다.

이를 수정할 수 있는 속성이 flex-wrap 이다.

<br>

```
body {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
```

![flow3](../../img/CSS/flow3.JPG)

flex-wrap 속성은 해당 flex 컨테이너가 다중라인 인지를 정하게 된다.

* flex-wrap: nowrap (기본값, 한 줄)
* flex-wrap: wrap (다중 라인)
* flex-wrap: wrap-reverse (다중 라인을 역순으로)

<br>

## flex-flow

* 단축 속성으로 하나의 속성을 통해 flex-direction, flex-wrap 을 설정함

```
body {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

body {
  display: flex;
  flex-flow: row wrap;
} // 위 와 같이 한번에 속성을 설정할 수 있음
```

<br>

## align-content

* 다중 라인 flex 컨테이너 에서 라인의 정렬을 설정할 때 사용
* 다중 라인이 아닐 경우엔 동작하지 않음
* 교차 축을 가로지르는 방향에서 항목을 이동시킴

#### 1. align-content: center

![ac1](../../img/CSS/ac1.JPG)

<br>

#### 2. align-content: flex-start

![ac2](../../img/CSS/ac2.JPG)

<br>

#### 31. align-content: flex-end

![ac3](../../img/CSS/ac3.JPG)

<br>

#### 4. align-content: space-between

![ac4](../../img/CSS/ac4.JPG)

<br>

#### 5. align-content: space-around

![ac5](../../img/CSS/ac5.JPG)

<br>

#### 6. align-content: space-evenly

![ac6](../../img/CSS/ac6.JPG)

<br>

## column-gap / row-gap

* 다중 라인일때 행과 열의 갭을 따로 줄 수 있다.

```
body {
  display: flex;
  row-gap: 10px; // 수평
  column-gap: 20px; // 수직
}
```

![gap1](../../img/CSS/gap1.JPG)

<br>

## Order / align-self

```
Flexbox는 대부분의 경우에는 Flex 부모에서 설정을 하지만, 
자식에게 적용하는 속성들이 몇개 있기는 하다

그 몇 안되는 속성중 두가지가 order, align-self 이다.
```

### Order
* 자식 요소들의 순서를 지정해주는 속성
* 기본 값은 0이다.

```
.box:nth-child(3) {
  background-color: blueviolet;
  order: 2;
}

.box:nth-child(6) {
  background-color: aqua;
  order: 1;
}
```

![order1](../../img/CSS/order1.JPG)

order 의 기본값은 0이므로, 기본 box 들이 0의 값으로 우선적으로 배치되고, 그리고 order 속성의 순차적으로 박스들이 배치된다.

### 음수도 적용될까?

```
.box:nth-child(6) {
  background-color: aqua;
  order: -1;
}
```

![order2](../../img/CSS/order2.JPG)

음수 역시도 잘 적용되어 order 속성의 순차적으로 배치되는 모습을 볼 수 있다.

<br>

### align-self
* flex 자식 항목에 주는 속성으로 교차축 정렬을 정할 수 있게 해줌

```
.box:nth-child(1) {
  align-self: flex-start;
}

.box:nth-child(3){
  align-self: flex-end;
}
```

![aself1](../../img/CSS/aself1.JPG)

<br>
<br>

# Refer
* nomadcoders - CSS Layout 마스터클래스

