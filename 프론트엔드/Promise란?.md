# Promise란?

-   `Promise`는 JavaScript에서 비동기 작업을 처리하기 위한 객체
-   비동기 작업이 완료되었을 때 성공(`resolve`) 또는 실패(`reject`) 상태를 나타내며, 해당 결과를 처리할 수 있는 메서드를 제공함

## Promise의 기본 개념

### Promise의 상태

Promise는 세가지 상태를 가짐

1. `pending`: 초기 상태로, 아직 작업이 완료되지 않음
2. `fulfilled`: 작업이 성공적으로 완료되었고, 결과를 반환(resolve)함
3. `rejected`: 작업이 실패했으며 이유를 반환(reject)함

### Promise의 라이프사이클

1. Promise는 `pending` 상태로 시작
2. 작업이 완료되면 `resolve`를 호출하여 상태를 `fulfilled`로 변경하거나, `reject`를 호출하여 상태를 rejected로 변경함
3. 한 번 상태가 바뀌면(`fulfilled` 또는 `rejected`) 다시 변경되지 않음

## Prmise 사용법

### Promise 생성

Promise는 생성자로 만들 수 있으며, 생성자에는 `executor`함수가 필요함
이 함수는 두개의 매개변수(`resolve`, `reject`)를 받음

```
const myPromise = new Promise((resolve, reject) => {
    // 비동기 작업
const success = true; // 성공 여부를 나타내는 조건

    if (success) {
        resolve("작업 성공"); // 작업이 성공했을 때 호출
    } else {
        reject("작업 실패"); // 작업이 실패했을 때 호출
    }

});
```

## then, catch, finally 사용

1. then
   Promise가 성공적으로 완료(`fulfilled`)되었을 때 실행할 코드를 작성함

```
myPromise.then((result) => {
    console.log(result)l // 출력: "작업 성공"
});
```

2. catch
   Promiser가 실패(`rejected`)했을 때 실행할 코드를 작성함

```
myPromise.catch((error) => {
    console.error(error); // 출력: "작업 실패"
});
```

3. finally
   Promise가 완료(`fulfilled` 또는 `rejected`)되었을 때 항상 실행

```
myPromise.finally(() => {
    console.log("작업이 종료되었습니다.");
});
```

## 실전 예제

### 1. 비동기 작업: 타이머

```
const wait = (ms) => new Promise((resolve) => seTimeout(resulove, ms));

wait(1000).then(() => {
    console.log("1초 후 실행됩니다.")
})
```

### API 호출

```
const fetchData = () => {
    return new Promise((resolve, reject) => {
        const success = true;

        setTimeout(() => {
            if (success) {
                resolve({ data: "서버 데이터"});
            } else {
                reject("서버 에러");
            }
        }, 1000);
    });
};

fetchData()
    .then((result) => {
        console.log("응답 성공:", result);
    })
    .catch((error) => {
        console.error("응답 실패", error);
    })
```

## Promise 체이닝

then 메서드를 사용하여 여러 비동기 작업을 순차적으로 처리할 수 있음

### 예제: 순차 처리

```
const fetchData = (id) => new Promise((resolve) => {
    setTimeout(() => resolve(`데이터 ${id}`), 1000);
});

fetchData(1)
    .then((result) => {
        console.log(result); // 출력: "데이터 1"
        return fetchData(2); // 다음 작업 반환
    })
    .then((result) => {
        console.log(result); // 출력: "데이터 2"
        return fetchData(3); // 다음 작업 반환
    })
    .then((result) => {
        console.log(result); // 출력: "데이터 3"
    })
    .finally(() => {
        console.log("모든 작업 완료");
    });
```

## Promise의 정적 메서드

1. Promise.all
   모든 Promise가 완료될 때까지 기다리고, 결과를 배열로 반환함

```
const p1 = Promise.resolve(1);
const p2 = Promise.resolve(2);
const p3 = Promise.resolve(3);

Promise.all([p1, p2, p3]).then((results) => {
    console.log(results); // 출력: [1, 2, 3]
});
```

2. Promise.race
   가장 먼저 완료된 Promise의 결과를 반환함

```
const p1 = new Promise((resolve) => setTimeout(resolve, 100, "첫 번째"));
const p2 = new Promise((resolve) => setTimeout(resolve, 200, "두 번째"));

Promise.race([p1, p2]).then((result) => {
    console.log(result); // 출력: "첫 번째"
});
```

3. Promise.allSettled
   모든 Promise가 완료될 때까지 기다리고, 각각의 상태와 결과를 반환함

```
const p1 = Promise.resolve("성공");
const p2 = Promise.reject("실패");

Promise.allSettled([p1, p2]).then((results) => {
    console.log(results);
    /*
    출력:
    [
        { status: "fulfilled", value: "성공" },
        { status: "rejected", reason: "실패" }
    ]
    */
})
```

## async/await와의 관계

async/awiat는 Promise를 더 간결하게 사용할 수 있는 문법

예제

```
const fetchData = () =>
    new Promise((resolve, reject) => {
        setTimeout(() => resolve("데이터"), 1000)
    });

async function getData() {
    try {
        const result = await fetchData();
        console.log(result); // 출력: "데이터"
    } catch (error) {
        console.error(error);
    }
}

getData();
```
