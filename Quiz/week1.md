# 1주차 퀴즈

## Q1. 가비지 콜렉터란 무엇인지 서술하세요.

A1. 애플리케이션이 할당한 메모리 공간을 주기적으로 검사하여 더 이상 사용되지 않는 메모리를 해제하는 기능이다. 더 이상 사용되지 않는 메모리란 어떤 식별자도 참조하지 않는 메모리 공간을 의미한다. 자바스크립트는 가비지 콜렉터를 내장하고 있는 매니지드 언어로서 가비지 콜렉터를 통해 메모리 누수(memory leak)를 방지한다.

## Q2. 동등 비교(==) 연산자와 일치 비교(===) 연산자의 차이점을 서술하세요.

A2. 동등 비교 연산자는 좌항과 우항의 피연산자를 비교할 때 먼저 암묵적 타입 변환을 통해 타입을 일치시킨 후에 같은 값인지 비교한다. 반면, 일치 비교 연산자는 암묵적 타입 변환을 하지 않고 좌항과 우항의 피연산자가 타입도 같고 값도 같은지 비교한다.

## Q3. 자바스크립트는 동적 타입 언어와 정적 타입 언어 중 어떤 언어인지 서술하고 해당 언어의 특징을 서술하세요.

A3. 자바스크립트는 동적 타입 언어로 변수를 선언할 때 타입을 선언하지 않고 var, let, const 키워드를 사용해 변수를 선언한다. 동적 타입 언어의 변수는 선언이 아닌 할당에 의해 타입이 결정되며, 재할당에 의해 변수의 타입이 언제든 동적으로 변할 수 있다.

## Q4. 데이터 타입이 필요한 이유를 서술하세요.

A4. 데이터 타입은 값을 저장할 때 확보해야 하는 메모리 공간의 크기를 결정하기 위해, 값을 참조할 때 한 번에 읽어 들여야 할 메모리 공간의 크기를 결정하기 위해, 메모리에서 읽어 들인 2진수를 어떻게 해석할지 결정하기 위해 필요하다.
