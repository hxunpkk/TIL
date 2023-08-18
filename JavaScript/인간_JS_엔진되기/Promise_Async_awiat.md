## 비동기
비동기란? 동시의 개념이 아님. 순서의 문제. <br>
한 번 비동기는 영원한 비동기. <br>

## Promise

### Promise?
+ 내용이 실행은 되었지만 결과를 아직 반환하지 않은 객체
+ Then을 붙이면 결과를 반환함
+ 실행이 완료되지 않았으면 완료된 후에 Then 내부 함수가 실행됨

```
const condition = true;
const promise = new Promise((resolve, reject) => {
    if (condition) {
        resolve('성공');
    } else {
        reject('실패');
    }
})
promise.
    then((message) => {
        console.log(message);
    })
    .catch((error) => {
        console.error(error);
    })
```
+ Resolve(성공리턴값) -> then으로 연결
+ Reject(실패리턴값) -> catch로 연결
+ Finally 부분은 무조건 실행됨

<br>

Promise는 Callback과 다르게 코드를 분리하여 작성할 수 있다.

callback의 경우엔 비동기 콜백을 작성할 때 결과를 분리할 수 없으나 promise 는 결과를 분리하여 원할때 해당 값을 사용할 수 있다.

콜백 헬의 문제점은 코드의 가독성도 있지만 가장 중요한점은 결과값을 바로 받아야 한다는 점! 그러나 Promise 는 나중에 활용이 가능하다.
```
const promise = setTimeoutPromise(3000)

console.log('딴짓');
console.log('딴짓');
console.log('딴짓');
console.log('딴짓');
console.log('딴짓');
console.log('딴짓');

promise.then(() => {
    지금 할래
});
```

<br>

📝 콜백 패턴 (3중첩)을 프로미스로 바꾸는 예제
```
fucntion findAndSaveUser(Users) {
    Users.findOne({}, (err, user) => { // 첫 번째 콜백
        if (err) {
            return console.error(err);
        }
        user.name = 'zero';
        user.save ((err) => { // 두 번째 콜백
            if (err) {
                return console.error(err);
            }
            Users.findOne({ gender: 'm' }, (err, user) => { // 세 번째 콜백
                // 생략
            })
        });
    });
}
```
findOne, save 메서드가 프로미스를 지원한다고 가정
```
function findAndSaveUser(Users) {
    Users.findOne({})
        .then((user) => {
            user.name = 'zero';
            return user.save();
        })
        .then((user) => {
            return Users.findOne({ gender: 'm' });
        })
        .then((user) => {
            // 생략
        })
        .catch(err => {
            console.error(err);
        })
}
```

<br>

### Promise.all(배열)
여러 개의 프로미스를 동시에 실행

❗ 단, 하나라도 실패하면 catch로 감.

```
const promise1 = Promise.resolve('성공1');
const promise2 = Promise.resolve('성공2');
Promise.all([promise1, promise2])
    .then((result) => {
        console.log(result); // ['성공1', '성공2']
    })
    .catch((error) => {
        cosonle.error(error);
    })
```
```
const p1 = axios.get('서버주소1')
const p2 = axios.get('서버주소2')
const p3 = axios.get('서버주소3')
const p4 = axios.get('서버주소4')
const p5 = axios.get('서버주소5')
const p6 = axios.get('서버주소6')

Promise.all([p1, p2, p3, p4, p5, p6]).then((results) => {}).catch((error) => {});
```

❗ 위와 같은 단점을 보완하기 위해 allSettled를 활용해 실패한 것만 추려낼 수 있음.

```
Promise.allSettled([p1, p2, p3, p4, p5, p6]).then((results) => {}).catch((error) => {});
```


<br>

## Async/await

문단 첫 예시 코드를 async function을 통해 더 간략하게 줄일 수 있음
+ 변수 = await 프로미스; 인 경우 프로미스가 resolve된 값이 변수에 저장
+ 변수 await 값; 인 경우 그 값이 변수에 저장
+ Async/await 코드는 오른쪽에서 왼쪽으로 해석하면 좋음.
```
async function findAndSaveUser(Users) {
    let user = await Users.findOne({});
    user.name = 'zero';
    user = await user.save();
    user = await User.findOne({ gender: 'm' });
    // 생략
}
```


❗ Async 함수는 항상 promise를 반환(return)

return의 값을 받고 싶으면 아래처럼 작성
```
async function main() {
    const result = await promise;
    return result;
}

main().then((name) => ...)
// 또는
const name = await main()
```

<br>

❗ reject 캐치를 위해서는 try catch 문을 통하여 에러 구문 작성
```
async function main() {
    try {
        const result = await promise;
        return result;
    } catch(error) {
        console.error(error);
    }
}
```

<br>

❗ 화살표 함수도 async/await 가능
```
const findAndSaveUser = async (Users) => {
    try {
        let user = await Users.findOne({});
        user.name = 'zero';
        user = await user.save();
        user = await Users.findOne({ gender: 'm' });
        //생략
    } catch (error) {
        console.error(error);
    }
};
```

<br>

❗ for await (변수 of 프로미스배열)
+ 노드 10부터 지원
+ resolve 된 프로미스가 변수에 담겨 나옴
+ await 을 사용하기 때문에 async 함수 안에서 해야함.


```
const promise1 = Promise.resolve('성공1');
const promise2 = Promise.resolve('성공2');
(async () => {
    for await (promise of [promise1, promise2] {
        console.log(promise);
    })
})();
```

<br>
<br>

# Refer
Youtube Zerocho TV - 인간 JS 엔진 되기

