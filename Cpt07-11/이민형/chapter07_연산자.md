## 7장 연산자

- 피연산자: 연산의 대상. 피연산자는 값으로 평가될 수 있는 표현식이어야 함.

### 7.1 산술 연산자

- 산술 연산이 불가능한 경우, NaN을 반환

#### \_\_7.1.1 이항 산술 연산자

- 2개의 피연산자를 산술 연산
- +, -, \*, /, %

#### \_\_7.1.2 단항 산술 연산자

- ++, --, +, -
- 증가/감소(++, --) 연산자의 위치 의미

  - 전위 증가/감소: 먼저 피연산자의 값을 증가/감소 연산 후 다른 연산 수행
  - 후위 증가/감소: 다른 연산을 먼저 수행한 후 피연산자의 값 증가/감소 연산

- 숫자 타입이 아닌 피연산자에 +/- 단항 연산자를 사용하면 피연산자를 숫자 타입으로 변환하여 반환

```javascript
// +
var x = "1";
console.log(+x); // 1

x = true;
console.log(+x); // 1

x = false;
console.log(+x); // 0

x = "Hello";
console.log(+x); // NaN
```

```javascript
// -
-"10"; // -10
-true; // -1
-"Hello"; // NaN
```

#### \_\_7.1.3 문자열 연결 연산자

- - 연산자는 피연산자 중 하나 이상이 문자열인 경우 문자열 연결 연산자로 동작

```javascript
"1" + 2; // '12'
1 + true; // 2 (true를 숫자로 변환해서 산술 연산함.)
1 + null; // 1 (null은 0으로 타입 변환됨.)
+undefined; // NaN
1 + undefined; // NaN
```

<hr>

### 7.2 할당 연산자

- 좌항의 변수에 우항의 값을 할당

| 연산자 |
| ------ |
| =      |
| +=     |
| -=     |
| \*=    |
| /=     |
| %=     |

- 할당문은 표현식인 문 ➡️ 연쇄 할당도 가능하다.

```javascript
var a, b, c;
a = b = c = 0;
console.log(a, b, c); // 0 0 0
```

<hr>

### 7.3 비교 연산자

#### \_\_7.3.1 동등/일치 비교 연산자

| 연산자 | 의미        | 설명             |
| ------ | ----------- | ---------------- |
| ==     | 동등 비교   | 값이 같음        |
| ===    | 일치 비교   | 값과 타입이 같음 |
| !=     | 부동등 비교 | 값이 다름        |
| !==    | 불일치 비교 | 값과 타입이 다름 |

- 동등 비교(==) 연산자는 비교하기 전 암묵적 타입 변환을 통해 타입을 일치시키고 값이 같은지 비교한다.

```javascript
5 == 5; // true
5 == "5"; // true
```

```javascript
"0" == ""; // false
0 == ""; // true
0 == "0"; // true
false == "false"; // false
false == "0"; // true
false == null; // false
false == undefined; // false
```

- 일치 비교(===) 연산자는 암묵적 타입 변환을 하지 않고 값을 비교한다.

🚨 주의: NaN은 자신과 일치하지 않는 유일한 값이다.

```javascript
NaN === NaN; // false
```

NaN인지 조사하려면 빌트인 함수 Number.isNaN 함수를 사용한다.

🚨0도 주의 (양의 0, 음의 0)

```javascript
0 === -0; // true
0 == -0; // true
```

#### \_\_7.3.2 대소 관계 비교 연산자

| 연산자 |
| ------ |
| >      |
| <      |
| >=     |
| <=     |

<hr>

### 7.4 삼항 조건 연산자

> 조건식 ? 조건식이 true일 때 반환 값 : 조건식이 false일 때 반환 값

- 삼항 조건 연산자 표현식은 값으로 평가할 수 있는 표현식인 문이다.
- if ... else 문은 값처럼 사용할 수 없다.

<hr>

### 7.5 논리 연산자

- ||, &&, !
- 논리 부정(!) 연산자는 언제나 불리언 값을 반환한다. 피연산자가 불리언 값이 아니면 불리언 타입으로 암묵적 타입 변환된다.

- 논리합(||), 논리곱(&&) 연산자 표현식의 평가 결과는 불리언 값이 아닐 수도 있다. 언제나 2개의 피연산자 중 어느 한쪽으로 평가된다.

<hr>

### 7.6 쉼표 연산자

왼쪽부터 차례대로 피연산자 평가, 마지막 피연산자의 평가가 끝나면 마지막 피연산자의 평가 결과를 반환한다.

<hr>

### 7.7 그룹 연산자

- ()
- 그룹 연산자의 우선순위가 가장 높다.

<hr>

### 7.8 typeof 연산자

- 피연산자의 데이터 타입을 문자열로 반환한다.

🚨null의 typeof 반환 갑은 "null"이 아닌 "object"이다. ➡️ 자바스크립트 첫 번쨰 버전의 버그

```javascript
console.log(typeof null); // object
```

<hr>

### 7.9 지수 연산자

- \*\*

<hr>

### 7.10 그 외의 연산자

- 뒤 챕터에서 자세하게 다룸!

| 연산자     | 내용                                                        |
| ---------- | ----------------------------------------------------------- |
| ?.         | 옵셔널 체이닝 연산자                                        |
| ??         | null 병합 연산자                                            |
| delete     | 프로퍼티 삭제                                               |
| new        | 생성자 함수 호출할 때 사용하여 인스턴스 생성                |
| instanceof | 좌변의 객체가 우변의 생성자 함수와 연결된 인스턴스인지 판별 |
| in         | 프로퍼티 존재 확인                                          |

<hr>

### 7.11 연산자의 부수 효과

- 일부 연산자는 다른 코드에 영향을 주는 부수 효과가 있다.
  - 할당 연산자
  - 증가/감소 단항 연산자
  - delete: 객체의 프로퍼티를 삭제하는 부수 효과

<hr>

### 7.12 연산자 우선순위

| 우선순위 | 연산자                                                      |
| -------- | ----------------------------------------------------------- |
| 1        | ()                                                          |
| 2        | new(매개변수 존재), ., [](프로퍼티 접근), ()(함수 호출), ?. |
| 3        | new(매개변수 미존재)                                        |
| 4        | x++, x--                                                    |
| 5        | !x, +x, -x, ++x, --x, typeof, delete                        |
| 6        | \*\*                                                        |
| 7        | \*, /, %                                                    |
| 8        | +, -                                                        |
| 9        | <, <=, >, >=, in, instanceof                                |
| 10       | ==, !=, ===, !==                                            |
| 11       | ??                                                          |
| 12       | &&                                                          |
| 13       | \|\                                                         |
| 14       | ? ... : ...                                                 |
| 15       | 할당 연산자                                                 |
| 16       | ,                                                           |

<hr>

### 7.13 연산자 결합 순서
