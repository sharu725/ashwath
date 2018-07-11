---



layout: post

title:  20180705 AJAX_jQuery

description: This is things that I learned. These are about AJAX and jQuery.

categories: jQuery

date: 2018-07-05

author: PaulLee



---



##2018년 7월 5일 AJAX_jQuery 필기



### 1. jQuery의 Ajax 메소드

1. get() : Get 방식으로 ajax 전송
2. getJSON() : Get 방식으로 전송하고 JSON 형식 응답받음
3. getScript() : Get 방식으로 전송하고 javaScript 형식 응답받음
4. post() : Post 방식으로 ajax 전송
5. load() : 결과를 HTML 형식으로 응답받음

### 2. jquery 내 Ajax 사용하기

```javascript
$('id').click(function() {
	$.ajax({
    	//1. get, post 방식
        type : '',
        //2. 요청 주소
        url : '',
        //3. 데이터
        data : '',
        //4. 데이터 타입
        dataType : '',
        //4. 성공 했을 때 동작
        success : function() {
        
        }
        //5. 실패 했을 때 동작
        error : function() {
        
        }
		// 등등
    })
})
```

***

### 3. 요소 찾기
```javascript
$(data).find('student').each(function() {
alert($(this).find('name').text());
});
```

코드 설명
$(data).find('student').each(function()
1. data 라는 문서 객체에서
2. student 라는 요소를 찾는데
3. 여러개 이므로 each 문을 사용


