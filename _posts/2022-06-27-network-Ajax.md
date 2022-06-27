---
layout: single
title: "[HTTP/네트워크] Ajax"
categories:
  - 네트워크 
tags:
  - 네트워크   
  - HTTP

---

### HTTP

**하이퍼텍스트 전송 프로토콜(HTTP)** 은 HTML과 같은 하이퍼미디어 문서를 전송하기위한 애플리케이션 레이어프로토콜이다. 클라이언트와 서버가 송수신을 하기 위한 표준 프로토콜이다. 

<u>프로토콜이란 ? 컴퓨터 내부나 컴퓨터 사이에서 데이터 교환을 정의하는 규칙체계이다.</u>



### Ajax 

**AJAX (Asynchronous JavaScript and XML)** 는 말 그대로 JavaScript와 XML을 이용한 비동기적으로 데이터를 요청하고, 서버가 응답한 데이터를 수신하여 웹페이지를 동적으로 갱신하는 프로그래밍 기법이다. 전통적인 웹페이지 생명주기는 아래와 같은 단점을 가지고 있다. (Ajax 이전)

1. 변경할 필요가 없는 부분까지 포함하여 페이지를 재렌더링 하였고 (불필요한 데이터 통신 발생)
2. 이로 인해 화면 전환이 일어나면 화면이 순간적으로 깜빡이는 현상이 발생한다. 
3. 클라이언트와 서버와의 통신이 동기방식으로 동작하기 때문에 서버로 부터 응답이 있을때까지 다음 처리는 블로킹 된다.

Ajax가 등장한 이후 필요한 데이터만 비동기적으로 전송받아 웹페이지의 변경될 필요가 없는 부분은 다시 렌더링하지 않고 필요한 부분만 렌더링 할 수 있게 된 것이다. 예를 들면 무한 스크롤이나 게시물에 좋아요를 눌렀을때 화면전환이 일어나지 않고 해당 데이터만 변경된다. -> 데이터를 패치로 받고 목록을 이동하는 웹을 만들었었는데 그때는 Ajax인지 몰랐다..

 

### Fetch API

Ajax를 사용하기 위해서 XMLHttpRequest, Fetch, jQuery 등의 방법이 있다. 우선 XMLHttpRequest는 동기적이고 Fetch보다 사용법도 복잡해서 Fetch를 주로 사용한다고 한다. (XMLHttpRequest는 사용해보지 못했고 예제만 봤었다)

 Fetch() 메서드를 통해 네트워크 리소스를 비동기적으로 가져올 수 있다.  (아래코드 [MDN 예제](https://developer.mozilla.org/ko/docs/Web/API/Fetch_API/Using_Fetch))

```js
fetch('http://example.com/movies.json')
  .then((response) => response.json())
  .then((data) => console.log(data));
```



### JSON

**JSON (JavaScript Object Notation)** 은 경량의 DATA-교환 형식이다. 이 형식은 사람이 읽고 쓰기에도 용이하다는 장점이 있다. JSON은 서버로 데이터를 보내거나 받을 때 사용하는데 "키-값 쌍"으로 이루어진 데이터 오브젝트를 전달한다. 언어 독립적인 형태이기 때문에 댑분의 프로그래밍 언어에서 사용할 수 있다. JSON을 사용하기 위해서는 정해진 규격을 지켜야 한다.

* object는 `{`좌 중괄호로 시작하고 `}`우 중괄호로 끝내어 표현한다. 각 name 뒤에 `:`colon을 붙이고 `,`comma로 name/value 쌍들 간을 구분한다.
* *array*은 값들의 순서화된 collection 이다. array는 `[`left bracket로 시작해서 `]`right bracket로 끝내어 표현한다. `,`comma로 array의 값들을 구분한다.
* *value*는 큰따옴표안에 *string*, *number* ,`true` ,`false` , `null`, *object* ,*array*이 올수 있다. 이러한 구조들을 포함한다.

```js
 {
    "id": "01",
    "name": "강혜원",
    "age": 24
 }
```



#### JSON.stringify()

`JSON.stringify()` 메서드는 JavaScript 값이나 객체를 JSON 문자열로 변환한다. 이것은 서버로 데이터를 보낼때 사용하게 된다. 

```js
console.log(JSON.stringify({ x: 5, y: 6 })); 
// expected output: "{"x":5,"y":6}"

console.log(JSON.stringify([new Number(3), new String('false'), new Boolean(false)]));
// expected output: "[3,"false",false]"
```



#### JSON.parse()

`SON.parse()` 메서드는 JSON 문자열의 구문을 분석하고, 그 결과에서 JavaScript 값이나 객체를 생성한다. 이것은 서버에서 데이터를 가져올때 사용된다.

```js
const json = '{"result":true, "count":42}';
const obj = JSON.parse(json);

console.log(obj.count);
// expected output: 42

console.log(obj.result);
// expected output: true
```



요약해보면 `Ajax`는 비동기적으로 데이터를 처리하는 프로그래밍 기법이고 이를 사용하기 위해서는 데이터를 받아올때 `Fetch API`를 사용하게 되며 이때 데이터를` Json` 형태로 받게 되는 것이다!

</br>

</br>









**참고 사이트 **

* [Fetch API (MDN)](https://developer.mozilla.org/ko/docs/Web/API/Fetch_API/Using_Fetch)
* [JSON](https://www.json.org/json-ko.html)

















