# 6주차 퀴즈

## 1. Rest 파라미터의 사용 이유를 arguments 객체와 관련해 설명하세요.

ES5에서는 가변 인자 함수에서 arguments 객체를 활용하여 전달받았다. arguments 객체는 유사 배열 객체이므로 배열 메서드를 사용하려면 Function.prototype.call이나 Function.prototype.apply 메서드를 사용해 객체를 배열로 변환해야 하는 과정을 거쳐야 한다.
<br>ES6에서는 rest 파라미터를 사용해 가변 인자 함수의 인수 목록을 배열로 직접 전달받을 수 있기 때문에 arguments 객체를 배열로 변환하는 번거로움을 피할 수 있다.
