---

layout: post
title:  20180627 javascript_3
description: This is things that I learned. These are basic content about javascript.
             (window, Element)
categories: javascript
date: 2018-06-27
author: PaulLee

---

##2018년 6월 27일 자바스크립트 필기


### 1. setTimeout / setInterval
1. setTimeout : 특정 기능을 지정한 시간 이후에 수행
   setTimeout(param1, param2) : param1(함수)을 param2(시간) 이후에 수행

2. setInterval : 특정 기능을 일정 시간 간격으로 계속 수행
   setInterval(param1, param2) : param1(함수)을 param2(시간) 간격으로 계속 수행
   - setInterval 종료하기
```
setTimeout(function() {
	clearInterval(id);
}, 5000); //5초 뒤에 setInterval 종료
```
***
### 2. 우선순위
```c
alert('a');
setTimeout(function() {
	alert('b');
}, 0);
alert('c');
```
**실행 순서 : a -> c -> b**
alert의 우선순위가 setTimeout 보다 높기 때문

***

### 모델
1. 문서객체모델(Document Object Model)
	- 보여지는 페이지 문서를 조작하는 객체
	- 자바스크립트의 핵심 활용 중 하나가 DOM 조작

2. 브라우저객체모델(Browser Object Model)
	- window, history, screen 등
	
```
window.onload = function() {
	var hello = document.getElementById('hello'); 
```
    
- window.onload : 소스를 다 읽고 실행
- document.getElementById(ID명)
   : html에서 element(요소)를 찾아와 ID값에 담음
	 자바스크립트로 화면에서 동적인 요소를 프로그래밍 하기 위해 많이 사용
     원하는 요소를 선택해 들고와서 어떤 이벤트가 발생하면 특정 속성값을 조작

```
	window.onload = function() {
		var header = document.createElement("h1");
        var textNode = document.createTextNode("제목입니다.");
        header.appendChild(textNode); 
		document.body.appendChild(header);
        }
```
- document.createElement("tag명") : 요소 노드 생성
- document.createTextNode("text") : 텍스트 노드 생성
- header.appendChild(textNode); : h1 요소에 text 노드를 연결
- document.body.appendChild(header); : body에 h1 요소 연결

***


### 문서객체 가져오기

1. ID를 통해서 가져오기
```c
	var header_1 = document.getElementById('header_1');
	header_1.innerHTML = "여기는 헤더1";
```
- document.getElementById('header_1'); : id값을 통해 Body에 있는 'header_1' 이라는 요소를 가져옴
- header_1.innerHTML = "여기는 헤더1"; : 'header_1' 의 값을 "여기는 헤더1" 이라는 텍스트로 변경

2. 태그를 통해서 가져오기
```c
	var headers = document.getElementsByTagName("h1");
	for(var i=0; i<headers.length; i++) {
		headers[i].innerHTML = "체체체체체인지" + headers[i];
		}
```
- document.getElementsByTagName("태그명");
	Body 부분이 태그명을 통해 요소를 가져옴, 값이 여러개일 경우 배열 상태로 넘어옴
> NodeList는 단순 배열이 아니기 때문에 인덱스 말고도 여러 키 값이 존재
> 모든 키 값이 필요하지 않기 때문에 for-each문은 사용하지 않는다.
