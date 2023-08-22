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

## Array.prototype.copyWithin()
+ 배열의 일부를 얕게 복사한 뒤, 동일한 배열의 다른 위치에 덮어쓰고 그 배열을 반환
+ 크기(배열의 길이)를 수정하지 않고 반환합니다.

```
const array1 = ['a', 'b', 'c', 'd', 'e'];

console.log(array1.copyWithin(0, 3, 4));
//["d", "b", "c", "d", "e"]

console.log(array1.copyWithin(1, 3));
//["d", "d", "e", "d", "e"]

[1, 2, 3, 4, 5].copyWithin(-2);
// [1, 2, 3, 1, 2]

[1, 2, 3, 4, 5].copyWithin(0, 3);
// [4, 5, 3, 4, 5]

[1, 2, 3, 4, 5].copyWithin(0, 3, 4);
// [4, 2, 3, 4, 5]

[1, 2, 3, 4, 5].copyWithin(-2, -3, -1);
// [1, 2, 3, 3, 4]
```

<br>

## Array.prototype.entries()
+ 배열의 각 인덱스에 대한 키/값 쌍을 가지는 새로운 Array Iterator 객체를 반환.
  - 이터레이터(Iterator)? => 반복 처리가 가능한 객체

```
const a = ["a", "b", "c"];

for (const [index, element] of a.entries()) {
  console.log(index, element);
}

// 0 'a'
// 1 'b'
// 2 'c'
```
```
const array = ["a", "b", "c"];
const arrayEntries = array.entries();

for (const element of arrayEntries) {
  console.log(element);
}

// [0, 'a']
// [1, 'b']
// [2, 'c']
```

<br>

## Array.prototype.every()
+ 배열 안의 모든 요소가 주어진 판별 함수를 통과하는지 테스트를 함
+ Boolean 값을 반환합니다.

```
const isBelowThreshold = (currentValue) => currentValue < 40;

const array1 = [1, 30, 39, 29, 10, 13];

console.log(array1.every(isBelowThreshold));
// true
```

<br>
<br>

# Refer
Array - Javascript | MDN https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array
