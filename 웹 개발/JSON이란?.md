# JSON이란?

JSON(JavaScript Object Notation)은 데이터를 저장하고 전송하기 위한 경량 데이터 형식
기본적으로 텍스트 기반이며, JavaScript 객체의 문법과 유사하지만, 언어에 독립적으로 사용될 수 있음

## 1.JSON의 특징

-   키-값 쌍 (Key-value Pair) 형식
-   텍스트 기반 포맷으로 사람이 읽고 쓰기 쉽고, 기계가 파싱하기 쉬움
-   경량 데이터 포맷으로 네트워크에서 데이터를 빠르게 전송할 수 있음
-   언어 독립적: Python, Java, C++, PHP 등 다양한 언어에서 사용 가능

## 2.JSON의 기본 문법

JSON 데이터는 `객체(Object)`와 `배열(Array)`을 기반으로 구성됨

1. JSON 객체 (Obejct)

-   중괄호 {}로 감싸고, `"키": 값` 형식으로 데이터를 저장함
-   키는 항상 문자열이어야 하며, 값은 문자열, 숫자, 불리언, 배열, 객체, null을 가질수 있음

```
{
    "name": "Alice",
    "age": 25,
    "isStudent": false
}
```

2. JSON 배열 (Array)

-   대괄호 []로 감싸고, 여러개의 값을 저장할 수 있음

```
{
    "students": [
        {"name": "Alice", "age": 25},
        {"name": "Bob", "age": 30},
        {"name": "Cha", "age": 28}
    ]
}
```

## 3.JSON의 특징

데이터 타입: 문자열, 숫자, 불리언, 객체, 배열, null등이 가능
키(Key): 항상 문자열 `" "`
값(Value): 문자열, 숫자, 불리언 등
주석(COmment): 지원하지 않음

## 4.JSON 변환 (파싱 & 문자열화)

JSON은 문자열 형태이므로, JavaScript에서 `객체로 변환(parse)`하거나,
반대로 `객체를 JSON문자열(stringify)`로 변환할 수 있음

### JSON 문자열 -> JavaSciprt 객체 (JSON.parse())

```
const jsonString = '{"name": "Alice", "age": 25}';
const user = JSON.parse(jsonString);

console.log(user.name); // Alice
console.log(user.age); // 25
```

### JavaSciprt 객체 -> JSON 문자열 (JSON.stringify())

```
const user = {
    name: "Alice",
    age: 25
}

const jsonString = JSON.stringify(user);
console.log(jsonString);
// '{"name":"Alice","age":25}'
```

## 5.JSON의 활용 예시

### 1. API 데이터 요청 및 응답

-   JSON은 웹 서버와 클라이언트 간의 데이터 전송 형식으로 가장 많이 사용됨

REST API 응답(JSON 형식)

```
{
    "status": "success",
    "data": {
        "user": {
            "id": 1
            "name": "Alice"
            "email": "alice@example.com"
        }
    }
}
```

Fetch API로 JSON 데이터 가져오기

```
fetch("https://api.example.com/user/1")
    .then(response => response.json()) // JSON -> 객체로 변환
    .then(data => console.log(data))
    .catch(error => console.error("Error":, error));
```

### 2. 로컬 스토리지에 데이터 저장

웹 브라우저의 localStorage에 JSON을 저장하고 가져올수 있음

```
const user = { name: "ALice", age: 25 };

// JSON을 문자열로 변환하여 저장
localStorage.setItem("user", JSON.stringify(user));

// JSON을 다시 객체로 변환하여 가져오기
const storedUser = JSON.parse(localStorage.getItem("user"));
console.log(storedUser.name); // 출력: Alice
```

### 3. JSON 파일 읽기(Node.js)

Node.js에서 JSON 파일을 읽고 JavaScript 객체로 변환 할수 있음

```
const fs = require('fs');

// JSON 파일 읽기
fs.readFile("data.json", "utf8", (err, data) => {
    if (err) {
        console.error("파일 읽는 중 오류 발생", err);
        retrun;
    }

    // JSON 객체로 변환
    const jsonData = JSON.parse(data);
    console.log(jsonData);
});
```

## 6. JSON의 장점과 단점

### 장점

-   1. 가벼온 데이터 형식: XML보다 간결하고 빠름.
-   2. 언어 독립적: JavaScript뿐만 아니라 Python, Java, PHP등 다양한 언어에서 사용 가능.
-   3. 가독성: 사람이 쉽게 읽고 쓸 수 있음.
-   4. 네트워크 전송 최적화: 텍스트 기반으로 HTTP 요청 및 응답에서 자주 사용됨.

### 단점

-   1. 보안 이슈: JSON.parse()를 사용할 떄 신뢰할 수 없는 데이터를 직접 실행하면 XSS 공격 가능성이 있음.
-   2. 주석 미지원: JSON은 주석을 허용하지 않아 코드 설명을 추가하기 어려움.
-   3. 데이터 타입 제한: undefined, Date, RegExp, Function 같은 타입을 저장할 수 없음.
