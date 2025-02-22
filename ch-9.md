# 타입 변환과 단축 평가

## 타입 변환

기존 원시 값을 사용해 다른 타입의 새로운 원시 값을 생성하는 것

### 명시적 타입 변환 (explicit coercion)

`타입 캐스팅 (type casting)`이라고도 하며, 개발자가 의도적으로 값의 타입을 변환하는 것이다.

### 암묵적 타입 변환 (implicit coercion)

`타입 강제 변환(type coercion)`이라고도 하며, 개발자의 의도와는 상관없이 표현식을 평가하는 도중에 자바스크립트 엔진에 의해 암묵적으로 타입이 자동 변환되기도 한다.

암묵적 타입 변환은 기존 변수 값을 재할당하여 변경하는 것이 아니라 피연산자의 값을 암묵적 타입 변환해 새로운 타입의 값을 만들어 단 한 번 사용하고 버린다.

## 암묵적 타입 변환

자바스크립트 엔진은 코드의 **문맥**을 고려해 암묵적으로 데이터 타입을 강제 변환할 때가 있다.

```
// 피연산자가 모두 문자열이어야 하는 문맥
'10' + 2; // '102'

// 피연산자가 모두 숫자 타입이어야 하는 문맥
10 * '5'; // 50

// 피연산자 또는 표현식이 불리언 타입이어야 하는 문맥
!0 // true
if (1) { }
```

### 문자열 타입으로 변환

```
1 + '2' // "12"
```

위 예제의 + 연산자는 피연산자 중 하나 이상이 문자열이므로 문자열 연결 연산자로 동작한다.

자바스크립트 엔진은 문자열 연결 연산자 표현식을 평가하기 위해 피연산자 중에서 문자열 타입이 아닌 피연산자를 문자열 타입으로 암묵적 타입 변환한다.

### 숫자 타입으로 변환

```
1 - '1'; // 0
1 * '10'; // 10
1 / 'one'; // NaN
```

산술 연산자의 모든 피연산자는 코드 문맥상 모두 숫자 타입어야 하므로 자바스크립트 엔진은 피연산자 중에 숫자 타입이 아닌 피연산자를 숫자 타입으로 암묵적 타입 변환한다.
<br>이때 피연산자를 숫자 타입으로 변환할 수 없는 경우는 산술 연산을 수행할 수 없으므로 평가 결과는 NaN이 된다.

```
'1' > 0 // true
```

비교 연산자의 모든 피연산자는 문맥상 모두 숫자 타입이어야 하므로 비교 연산자의 피연산자 중에 숫자 타입이 아닌 연산자를 숫자 타입으로 암묵적 타입 변환한다.

### 불리언 타입으로 변환

조건식은 불리언 값으로 평가되어야 하는 표현식이다.
<br>자바스크립트 엔진은 조건식의 평가 결과를 불리언 타입으로 암묵적 타입 변환한다.

자바스크립트 엔진은 불리언 타입이 아닌 값을 `Truthy 값(참으로 평가되는 값)` 또는 `Falsy 값(거짓으로 평가되는 값)`으로 구분한다.

> Falsy 값
>
> - flase
> - undefined
> - null
> - 0, -0
> - NaN
> - ''(빈 문자열)

Falsy 값 외의 모든 값은 모두 true로 평가되는 Thruthy 값이다.

## 명시적 타입 변환

1. `String` 생성자 함수를 new 연산자 없이 호출하는 방법

   ```
   String(1); // "1"
   String(NaN); // "NaN"
   String(Infinity); // "Infinity"

   String(true); // "true"
   String(false); // "false"
   ```

2. `Object.prototype.toString` 메서드를 사용하는 방법

   ```
   (1).toString(); // "1"
   (true).toString(); // "true"
   ```

3. `문자열 연결 연산자`를 이용하는 방법

   ```
   1 + ''; // "1"
   true + ''; // "true"
   ```

### 숫자 타입으로 변환

1. `Number` 생성자 함수를 new 연산자 없이 호출하는 방법

   ```
   Number.('0'); // 0
   Number.('-1'); // -1
   Number.('10.53'); // 10.53

   Number(true); // 1
   Number(false); // 0
   ```

2. `parseInt, parseFloat` 함수를 사용하는 방법

   ```
   parseInt('1'); // 1
   parseFloat('10.53') // 10.53
   ```

3. `+ 단항 산술 연산자`를 이용하는 방법

   ```
   +'0'; // 0
   +'-1'; // -1
   +'10.53'; // 10.53

   +true; // 1
   +flase; // 0
   ```

4. `* 산술 연산자`를 이용하는 방법

   ```
   '0' * 1; // 0
   '-1' * 1; // -1
   true * 1 // 1
   ```

### 불리언 타입으로 변환

1. `Boolean` 생성자 함수를 new 연산자 없이 호출하는 방법

   ```
   Boolean('x'); // true
   Boolean(''); // false
   Boolean('false') // true

   Boolean(0); // false
   Boolean(1); // true
   Boolean(NaN); // false
   Boolean(Infinity); // true

   Boolean(null); // false
   Boolean(undifined); // false

   Boolean({}); // true
   Boolean([]); // true
   ```

2. `! 부정 논리 연산자`를 두 번 사용하는 방법

   ```
   !!'x'; // true
   !!0; // false

   !!null; // flase

   !!{}; // true
   ```

## 단축 평가

### 논리 연산자를 사용한 단축 평가

논리곱(&&) 연산자와 논리합(||) 연산자의 평가 결과는 불리언 값이 아닐 수도 있고 2개의 피연산자 중 어느 한쪽으로 평가된다.

단축 평가(short-cirtcuit evaluation)는 논리 연산의 결과를 결정하는 피연산자를 타입 변환하지 않고 그대로 반환하는 것이다.
<br>단축 평가는 표현식을 평가하는 도중에 평과 결과가 확정된 경우 나머지 평가 과정을 생략한다.

| 단축 평가 표현식    | 평가 결과 |
| ------------------- | --------- |
| true \|\| anything  | true      |
| false \|\| anything | anything  |
| true && anything    | anything  |
| false && anything   | false     |

```
'Cat' || 'Dog' // 'Cat'이 true 이므로 문자열 'Cat'을 그대로 반환
false || 'Dog' // 'Dog'

'Cat' && 'Dog' // 'Dog'
flase && 'Dog' // false
```

어떤 조건이 Truthy 값일 대 무언가를 해야 한다면 논리곱 연산자 표현식으로 if문을 대체할 수 있다.

```
var done = true;
var message = '';

message = done && '완료';
console.log(message); // "완료"
```

조건이 Falsy 값일 때 무언가를 해야 한다면 논리합 연산자 표현식으로 if문을 대체할 수 있다.

```
var done = false;
var message = '';

message = done || '미완료'
console.log(message); // "미완료"
```

### 옵셔널 체이닝 연산자 (optional chaining)

`?.` 옵셔널 체이닝 연산자는 좌항의 피연산자가 null 또는 undefined인 경우 undefined를 반환하고, 그렇지 않으면 우항의 프로퍼티 참조를 이어간다.

```
var elem = null;

var value = elem?.value;
console.log(value); // undefined
```

> 옵셔널 체이닝 연산자 ?.는 객체를 가리키기를 기대하는 변수가 null 또는 undefined가 아닌지 확인하고 프로퍼티를 참조할 때 유용하다.

좌항 피연산자가 Falsy값이어도 null 또는 undefined가 아니면 우항의 프로퍼티 참조를 이어간다.

### null 병합 연산자 (nullish coalescing)

`??` null 병합 연산자는 좌항의 피연산자가 null 또는 undefined인 경우 우항의 피연산자를 반환하고, 그렇지 않으면 좌항의 피연산자를 반환한다.

```
var foo = null ?? 'default string';
console.log(foo); // "default string"
```

> null 병합 연산자 ??는 변수에 기본값을 설정할 때 유용하다.

좌항 피연산자가 Falsy값이어도 null 또는 undefined가 아니면 좌항의 피연산자를 그대로 반환한다.
