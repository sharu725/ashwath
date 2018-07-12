---



layout: post

title:  20180712 jQuery_json-2

description: use jQuery with Json

categories: jQuery

date: 2018-07-12

author: PaulLee



---



##2018년 7월 12일 비동기 방식 아이디 체크하기



### 1. In java

```java
@RequestMapping(value="idCheck.do", method=RequestMethod.GET)
	public void idCheck(HttpServletRequest request, HttpServletResponse response, String id) {
		response.setContentType("text/html; charset=UTF-8"); //문자 인코딩
		Customer customer = service.getCustomer(id);
		boolean result = customer == null ? true : false;
		String resultStr = "{\"result\" : " + result + "}";
		try {
			response.getWriter().println(resultStr);
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
	}
```

1. 파라미터로 받아온 id로 DB 내 존재 여부를 확인

2. JSON 방식의 문자열로 html Page로 전송


### 2. In html

```javascript
$('#id').keyup(function() {
			$.ajax ({
				type : 'get',
				url : 'customer.html/idCheck.do',
				data : $('#id'),
				dataType : 'json',
				success : function(result) {
						if(result.result)
								msg = "가입 가능한 아이디입니다.";
							else {
								msg="중복된 아이디입니다.";
							}
						 $('#isDupli').html(msg);
				},
				error : function(xhr, option, error) {
					console.log(xhr + "//" + error);
				}
			});
		});
```

1. id명이 'id' 인 input=text의 keyup 이벤트 요청
 
2. ajax 방식으로 요청 후 수행 메소드 실행
	- 아이디를 입력할 때마다 isDupli의 text값이 변경

***
