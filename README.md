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
GET https://www.zerocho.com HTTP/1.1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) ...
Upgrade-Insecure-Requests: 1

(본문 없음)

- 첫 줄은 시작줄입니다. GET 은 HTTP 메서드, https://www.zerocho.com 은 주소, HTTP/1.1은 HTTP 버젼입니다.
- 즉, 요청 메시지의 시작줄은 *메서드 주소 버전 으로 구성된다.

-두번째 줄 부터는 헤더이다. 요청에 대한 정보를 담고 있으며, User-Agent, Upgrade-Insecure-Requests 등등이 헤더에 해당된다.
- 헤더에서 한 줄 띄우고 본문이 시작된다, 본문은 요청을 할 때 함께 보낼 데이터를 담는 부분이며, 
- 위의 예제에선 주소로만 요청을 보내고 있어, 따로 데이터를 담아 보내지 않아 본문이 비어있다.

### 응답

ex)

HTTP/1.1 200 OK
Connection: keep-alive
Content-Encoding: gzip
Content-Length: 35653
Content-Type: text/html;

<!DOCTYPE html><html lang="ko" data-reactroot=""><head>
<title...>
          
- 요청과 마찬가지로 시작줄, 헤더, 본문으로 구성되어있다.
- 첫줄은   버전 상태코드 상태메세지로 구성되어있다. 
- 두번째

          
          
