---

layout: post
title:  20180625 javascript_2
description: This is things that I learned. These are basic content about javascript.
             (function, Object)
categories: javascript
date: 2018-06-26
author: PaulLee

---

##2018년 6월 26일 자바스크립트 필기


### 1. 변수에 함수를 담을 경우

```c
 function func() {
 	alert("func 호출");
	
 	var f = function() {
 		alert("func의 익명함수");
 	};
	
 	return f;
 }
 var result = func();
 result();
```

 - 변수에 함수를 담을 시 () 가 없으면 소스코드 자체가 변수에 담김
   () 가 있으면 담긴 함수를 실행
 - **func()(); //메소드 체인 기법(내부 함수 호출)**


***
### 2. 클로저
```c
var myFunc = function() {
	var hello = "Hello World";
	var inner = function() {
		alert(hello);
	};
	return inner;
}

var a = myFunc();
var b = myFunc();

a();
b();
```
** 클로저**
함수 내의 지역변수는 함수가 종료될 때 메모리가 해제되어야함
반환값으로 사용한 내부함수에서 그 지역변수를 사용하고 있어서 해제되지 못하고 남아있는 현상
클로저는 내부함수가 외부함수의 맥락에 접근 할 수 있는 것을 말함

***

### 자바스크립트 내장 함수
- 기본적으로 자바스크립트에서 제공하는 함수들 ex) alert, prompt 등

##### 인코딩, 디코딩 관련 함수 등


	◆ escape <--> unescape => 적절한 정도로 인코딩
	◆ 영문 알파벳, 숫자, 일부 특수문자를 제외한 모든 문자를 인코딩

	◆ encodeURI <--> decodeURI => 최소한의 문자만 인코딩
	◆ escape에서 인터넷 주소에 사용되는 일부 특수문자는 변환하지 않음

	◆ encodeURIComponent <--> decodeURIComponent => 대부분의 문자를 인코딩
	◆ 알파벳과 숫자를 제외한 모든 문자를 인코딩
	◆ UTF-8인 코딩과 같음 


##### 평가함수, 형변환함수 등


	◆ eval(String) : String에 들어있는 자바스크립트 코드를 실행
	◆ isFinite(number) : number에 들어있는 숫자가 무한한 값인지 확인
	◆ isNan(number) : number가 Nan인지 확인
	◆ Number(String) : String을 숫자로 바꿈, 전체를 바꿈 ex)1000원 => Nan
	◆ parseInt(String) : String을 정수로 바꿈, 한글자씩 읽어서 판단 ex)1000원 => 1000
	◆ parseFloat(String) : String을 실수로 바꿈

***


### 객체
```c
var obj = {
		이름 : 'Paul',
		나이 : '29',
		직업 : '백수'
};

alert(obj.이름); // '.' 은 자동완성 가능
alert('이름' in obj); //obj 객체 내의 이름의 값이 있는지 boolean 값을 리턴
```

```c
// var student = [];
// student.name = "Paul";
// student.age = 20;
// student.toString = function() {
// 	var output = '';
// 	output += '이름 : ' + this.name + '\n';
// 	output += '나이 : ' + this.age;
// 	return output;
// }

// alert(student.toString()); //저장된 output 문자열을 출력
// delete(student.age); //객체의 속성을 삭제
// alert(student); //자바에서처럼 toString 안쓰고 alert에 객체를 대입 시 toStiring 해줌
```
```c
function makeStudent(n, k, e, m) {
	
	b = 20; 
	n = 'Lee'; 
	this.n = 'Lee' 
    }
    ```
1. b = 20;
	**함수 내부에 b라는 변수가 없으므로 암시적으로 전역변수 b를 생성**

2. n = 'Lee';
	**함수 내부에 매개변수 n이 있으므로 지역변수 n에 'Lee'를 대입**
    
3. this.n = 'Lee'
	**this 키워드가 붙어있으므로 지역변수 n이 아니라 자기가 속해있는 객체의 속성(window 객체)**
 
>> 자바스크립트에서의 최상위 객체 : window

##### 생성자
```c
function Student(name, kor, eng, math) {
	this.name = name;
	this.kor = kor;
	this.eng = eng;
	this.math = math;
	this.getSum = function() {
		return this.kor + this.eng + this.math;
	}
} 
var s = new Student('Paul', 100, 100, 100);
```
**생성자로써 만든 함수 : 현재 객체가 아닌 새로운 객체를 만들어서 새로운 객체 내부에서 함수를 수행, 그리고 새로운 객체 리턴**