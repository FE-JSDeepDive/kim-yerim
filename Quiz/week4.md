# 4주차 퀴즈

## Q1. new 연산자의 유무에 따라 함수를 호출이 어떻게 달라지는지 서술하세요.

A1. new 연산자와 함께 함수를 호출하면 해당 함수는 생성자 함수로 동작하며 함수 객체의 내부 메서드 [[Constructor]]가 호출된다. new 연산자 없이 생성자 함수를 호출하면 일반 함수로 동작하며 [[Call]]이 호출된다.

## Q2. ESLint에서 Object.prototype의 빌트인 메서드를 객체가 직접 호출하는 것을 권장하지 않는 이유를 서술하세요.

A2. Object.prototype의 빌트인 메서드들은 모든 객체의 프로토타입 체인의 종점에 존재하는데 Object.create를 사용하면 프로토타입 체인의 종점 즉, Object.prototype의 앞에 객체를 생성할 수 있어 Object.prototype의 빌트인 메서드들을 사용할 수 없기 때문이다.
