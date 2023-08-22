## Array.prototype.at()
+ 배열에서 해당 값에 해당하는 인덱스의 요소를 반환 
+ 양수와 음수 모두 지정할 수 있고, 음수 값의 경우 배열의 뒤에서부터 인덱스를 카운트
+ 맨 마지막 요소를 가져오고 싶을 때 length 속성을 사용해 array[array.length - 1]을 하는 대신, 짧게 array.at(-1)을 사용할 수 있음

```
// 대상 배열
const cart = ["사과", "바나나", "배"];

// 주어진 배열의 마지막 요소를 반환하는 함수
function returnLast(arr) {
  return arr.at(-1);
}

// 위의 배열 'cart'에서 마지막 요소를 가져옴
const item1 = returnLast(cart);
console.log(item1); // '배' 기록

// 위의 배열 'cart'에 요소를 추가함
cart.push("오렌지");
const item2 = returnLast(cart);
console.log(item2); // '오렌지' 기록

cart.at(-2) // '배' 기록
```

<br>

## Array.prototype.concat()
+ 인자로 주어진 배열이나 값들을 기존 배열에 합쳐서 새 배열을 반환
+ 기존배열을 변경하지 않음
+ 추가된 새로운 배열을 반환

```
const alpha = ["a", "b", "c"];
const numeric = [1, 2, 3];

alpha.concat(numeric);
// 결과: ['a', 'b', 'c', 1, 2, 3]

const num1 = [1, 2, 3];
const num2 = [4, 5, 6];
const num3 = [7, 8, 9];

num1.concat(num2, num3);
// 결과: [1, 2, 3, 4, 5, 6, 7, 8, 9]

const beta = ["a", "b", "c"];

beta.concat(1, [2, 3]);
// 결과: ['a', 'b', 'c', 1, 2, 3]
```

<br>



<br>
<br>

# Refer
Array - Javascript | MDN https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array
