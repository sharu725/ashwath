---



layout: post

title:  20180711 jQuery_json

description: use jQuery with Json

categories: jQuery

date: 2018-07-11

author: PaulLee



---



##2018년 7월 11일 JSON 사용하기



### 1. In java

```java
	@RequestMapping("list.do")
	public void getList(HttpServletResponse response) {
		List<Customer> customerList = service.selectAll();
		HashMap<String, Object> map = new HashMap<String, Object>();
		map.put("customerList", customerList);
		JSONObject jsonObj = new JSONObject();
		jsonObj.putAll(map);
		try {
			response.getWriter().println(jsonObj);
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
	}
```

1. JSONObject : JSON 형태의 데이터를 관리해주는 메소드
2. JSONObject jsonObj = new JSONObject();
	- JSONObject형 jsonObj 생성
3. HashMap을 대입하기 위해 putAll 을 사용
4. response.getWriter().println(jsonObj);
	- println 을 사용하여 객체를 html 페이지 혹은 jsp 페이지로 전송


### 2. In html

```javascript
$.each(data.customerList, function(index, customerList) {};
```

1. jQuery.each(collection, callback(indexInArray, valueOfElement))
	- 특정한 집합을 반복문 형태로 사용
	- collection : Object 또는 Array
	- callback : 실행될 함수

2. collection 이 Map일 경우
	- indexInArray : key
	- valueOfElement : value

***
