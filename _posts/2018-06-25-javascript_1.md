---
layout: post
title:  20180625 Javascript_1
description: This is things that I learned. These are basic content about Javascript.
             (type, function)
categories: Javascript
date: 2018-06-25
author: PaulLee

---

##2018년 6월 25일 자바스크립트 필기


### 자바 스크립트란?  : 스크립트 프로그래밍 언어

>참고 - 인터프리터 : 한번에 한 줄씩 읽어서 실행, 컴파일 단계를 거치지 않음

***
### 자바스크립트 자료형
1. 숫자 자료형
2. 논리 자료형
3. 문자열 자료형
4. 함수형
5. 객체형
6. undefined

***

### 자바스크립트의 객체 : Key:Value 형태의 데이터
1. Key==글자 : 객체
2. Key==숫자(인덱스) : 배열

### 자바스크립트 함수 : 코드(명령어)의 집합을 나타내는 자료형
1. 선언함수
2. 익명함수


```c
function func() {
	alert("선언함수");
}

var func2 = function() {
	alert("익명함수");
}

func(); //선언함수 호출
func2(); //변수에 담아둔 익명함수 호출

```

***

### 매개변수

```c
function f(x) {
retunr x*x;
}
alert(f(1,2,3,4));

```

f함수는 매개변수를 하나만 받도록 설계. 매개변수를 여러개 전달은 다 됨.
다만 첫번째 매개변수만 x라는 이름을 갖게 되고 나머지는 이름이 없는 상태

**함수 선언 시 정해둔 매개변수보다 많은 변수가 들어오면 이름이 붙지 않은 채로 매개변수 값을 받아서 수행(arguments 객체를 통해서 이름 붙지 않은 매개변수에 접근 가능)**
```c
ex) function f(x) {
alert(arguments.length);
alert(arguments[1]);
retunr x*x;
}
alert(f(1,2,3,4));

출력값 : 4, 3
```

**함수 선언 시 정해둔 매개변수보다 적은 변수가 들어오면 붙여논 변수명에 값이 없으니 undefined 값이 들어있는 채로 함수를 진행**

***

### 내부함수
```c
function func() {
	function a() {
    	alert('func의 a');
    }
}
```

***

### 콜백함수

매개변수로 넘어온 값이
숫자면 산술연산 가능
문자열이면 결합연산 등 연산 가능
boolean이면 조건 연산 가능
배열이면 인덱스 접근 가능
객체면 멤버 접근 가능
함수면 **호출 가능**

```c
function callFiveTimes(func) {
	for(var i=0; i<5; i++)
    	func();
}

callFiveTimes(
	function() {
    	alert('호출!!!');
    }
);
```

**매개변수로 전달되어지는 함수를 <<콜백함수>>라고 한다**