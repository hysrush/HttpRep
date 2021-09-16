# HTTP란? 

- HTTP는 Hyper Text Transfer Protocol의 약자로, '인터넷에서 데이터를 주고받을 수 있는 프로토콜(규칙) 이다.
- 이렇게 규칙을 정해두었기 때문에, 모든 프로그램이 이 규칙에 맞춰 개발하여 서로 정보를 교환 할 수있다.

*서버의 역할 : 요청에 대한 응답을 보내주는 것.

- 요청을 보낼때는 요청에 대한 정보를 담아 서버로 보낸다. 식당에서 주문서 작성하는것과 같은 원리, 
- 서버가 주문서를 받아 클라이언트가 원하는 것을 파악할수 있다.

- 서버도 응답할때 응답에 대한 정보를 담아 클라이언트로 보낸다. 
- 이러한 정보가 담긴 메세지를 'HTTP 메세지' 라고 한다.
- HTTP 메세지는  시작줄, 헤더 , 본문으로 구성된다.

### 요청
ex)
- GET https://www.naver.com HTTP/1.1
- User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) ...
- Upgrade-Insecure-Requests: 1

(본문 없음)

- 첫 줄은 시작줄입니다. GET 은 HTTP 메서드, https://www.naver.com 은 주소, HTTP/1.1은 HTTP 버젼입니다.
- 즉, 요청 메시지의 시작줄은 *메서드 주소 버전 으로 구성된다.

-두번째 줄 부터는 헤더이다. 요청에 대한 정보를 담고 있으며, User-Agent, Upgrade-Insecure-Requests 등등이 헤더에 해당된다.
- 헤더에서 한 줄 띄우고 본문이 시작된다, 본문은 요청을 할 때 함께 보낼 데이터를 담는 부분이며, 
- 위의 예제에선 주소로만 요청을 보내고 있어, 따로 데이터를 담아 보내지 않아 본문이 비어있다.

### 응답

ex)
```html
> HTTP/1.1 200 OK
> Connection: keep-alive
> Content-Encoding: gzip
> Content-Length: 35653
> Content-Type: text/html

> <!DOCTYPE html><html lang="ko" data-reactroot=""><head>
```

        
- 요청과 마찬가지로 시작줄, 헤더, 본문으로 구성되어있다.
- 첫줄은   버전 상태코드 상태메세지로 구성되어있다. 
- 두번째 줄 부터는 헤더이며, 응답에 대한 정보를 담고있다.
- 응답에는 보통 본문이 있다. 보통 데이터를 요청하고, 응답메세지에는 요청한 데이터를 담아서 보내주기 때문
- 응답메세지에 html이 담겨있고, 이 html을 받아 브라우저가 화면에 렌더링 한다.

### HTTP 메서드란?

위의 GET/https://www.naver.com HTTP/1.1 에서.  인터넷 주소창에 주소를 치는 행위는, 해당 주소에 대해 GET 요청을 하는것이다.  
크롬 주소창에 WWW.NAVER.COM 이라고 치면 GET WWW.NAVER.COM HTTP/1.1 요청을 보내는 것과 같다  이런식으로, 요청을 할 때 주소와 함께 HTTP
메서드를 같이 보낼수 있으며  자주쓰는 메서드는 GET,POST,PUT,PATCH,DELETE 정도가 있으며(OPTIONS,HEAD,CONNECT,TRACE 등도 있다.)

### HTTP 헤더란?

- HTTP 헤더는 클라이언트와 서버가 요청 또는 응답으로 부가적인 정보를 전송할 수 있도록 해줍니다.  HTTP헤더는 대소문자를 구분하지 않는 이름과 콜론':' 다음에 오는 값으로 이루어져 있다. 값 앞에 붙은 빈 문자열은 무시된다.

-헤더를 세부적으로 나누면 4가지로 구성되어있다.
1) General header : 요청과 응답 모두에 적용되지만 바디에서 최종적으로 전송되는 데이터와는 관련이 없는 헤더.
2) Request header : 페치 될 리소스나 클라이언트 자체에 대한 자세한 정보를 포함하는 헤더. (요청 헤더)
3) Response header : 위치 또는 서버 자체에 대한 정보(이름, 버전 등 )과 같이 응답에 대한 부가적인 정보를 갖는 헤더(응답 헤더)
4) Entity header : 콘텐츠 길이나 MIME 타입과 같이 엔티티 바디에 대한 자세한 정보를 포함하는 헤더.

ex) 요청 헤더는 클라이언트 자체에 대한 자세한 정보를 포함한다.
GET /home.html HTTP/1.1  
Host: developer.mozilla.org  
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:50.0) Gecko/20100101 Firefox/50.0  
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8  
Accept-Language: en-US,en;q=0.5  
Accept-Encoding: gzip, deflate, br  


- GET 요청 하겠으며, 호스트이름은 developer.mozilla.org 라는 정보를 제공한다, Accept는 MIME타입으로 표현되는 클라이언트가 이해 가능한 콘텐츠 타입이 무엇인지를 알려준다, 예를들어 텍스트, 이미지, HTML을 표기해 타입을 알려주는 역할을 한다.

- 응답헤더는 HTTP 응답에서 사용될 수 있는 HTTP 헤더이다.  
ex)  
200 OK  
Access-Control-Allow-Origin: *  
Connection: Keep-Alive  
Content-Encoding: gzip  
Content-Type: text/html; charset=utf-8  
Date: Mon, 18 Jul 2016 16:06:00 GMT  
Etag: "c561c68d0ba92bbeb8b0f612a9199f722e3a621a"  
Keep-Alive: timeout=5, max=997  
Last-Modified: Mon, 18 Jul 2016 02:36:04 GMT  
Server: Apache  
Set-Cookie: mykey=myvalue; expires=Mon, 17-Jul-2017 16:06:00 GMT; Max-Age=31449600; Path=/; secure  

- 원래 호스트가 다르게 되면 아무 요청에 대해서 허가해주고 응답해주면 안되기 때문에,  
- 요청에 대해 허가가 없이는 정보를 전달해주지 않는다.  그렇기 때문에 응답 헤더로 Access-Control-Allow-Origin을 통해 허용하고, Access-Control-Allow-Method로 어떤 요청 GET인지 POST인지 요청을 서버에서 작성 한 후에 정보를 응답으로 보내 줄 수있다.

*헤더의 종류에 대한 자료 .https://www.zerocho.com/category/HTTP

          
          
