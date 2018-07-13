---
layout: post
title:  20180628 Javascript_4
description: This is things that I learned. These are basic content about javascript.
             (Element, Trigger, regular expression)
categories: Javascript
date: 2018-06-28
author: PaulLee

---

##2018년 6월 28일 자바스크립트 필기


### 1. 이벤트 실행 후 제거

```javascript
	var header = document.getElementById('header');
	header.onclick = function() {
		alert("클릭클릭")
		header.onclick=null;
        }
```
- **이벤트 제거 방법 : 속성값 제거(null값 대입)**
***
### 2. this
```javascript
	header.onclick = function(e) {
		alert(this)
		this.style.color = "pink";
		this.style.background = 'black';
		alert(e.x + ',' + e.y);
	}
```
- **이벤트 수행 함수에서의 this는 이벤트가 발생한 객체**

***

### 3. Trigger
#### 어떤 요소 노드의 이벤트 처리 함수에서 다른 요소 노드의 이벤트 처리 함수 호출

```javascript
	var btn1 = document.getElementById('btn1');
	var counter1 = document.getElementById('counter1');

	btn1.onclick = function() {
		counter1.innerHTML = Number(counter1.innerHTML) + 1;
	}
```
- btn1 클릭 이벤트 수행 시 counter1의 숫자 증가가 같이 수행

***


### 4. 이벤트 수행 범위

1. 부모 범위 실행 막기
```javascript
		document.getElementById('main').onclick = function() {
			alert('main div다');
		};
		document.getElementById('header').onclick = function(e) {
			alert('header다');
			if(e.stopPropagation()) {
				e.stopPropagation();
			}
        }

     <body>
       <div id="main" style="background-color: pink">
	<br>
		<h1 id = "header" style="background-color: green">What!!!</h1>
	<br>
	</div>
    </body>
```
**- e.stopPropagation() : 부모 범위의 이벤트 실행을 막아줌 **

2. eventListener
- 해당 이벤트를 실행하기 위해 대기
```javascript
	var header = document.getElementById('header');
	header.addEventListener('click', function(e) {
		alert("누름!!");e
	});
	header.addEventListener('click', function(e) {
		alert("또 누름?");
	});
```
	- 총알을 다 쓰고 리로드 할 시 필요할 듯 하다!!
	- eventListener 제거 : removeEventListner(이벤트명, 변수명);

***

### 5. 정규표현식
** 특정한 규칙을 가진 문자열의 집합을 표현하는 데 사용하는 형식 언어 **
```javascript
		var check = /^[a-z]$/; //소문자로 된 한글자 패턴
		var check = /^[a-z]{2}$/; //소문자로 된 두글자 패턴
		var check = /^[A-Z]{3}\d{5}$/;
        //대문자 A~Z까지 3글자, 숫자 5자리 패턴
		var check = /^[0-9]{3}[-][0-9]{3,4}[-][0-9]{4}$/;
        //전화번호 패턴
		var check = /^(\d{3})-(\d{3,4})-(\d{4})$/;
        //전화번호 패턴 다른 version
		var check = /(?=a)/;
        //a가 포함되었는지 체크
		var check = /(?=.*[a-z])(?=.*[A-Z])(?=.*[0-9])(?=.*[~!@#$%^&*()]).{8,}/;
        //8글자로 되고 위 조건의 문자들이 포함되는지 체크
```
