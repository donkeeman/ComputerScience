# 웹의 동작 방식
1. 사용자가 웹 브라우저 주소창에 방문할 웹 사이트의 주소(URL)를 입력
2. 웹 브라우저는 DNS 서버에서 웹 사이트의 진짜 주소(IP 주소)와 포트를 검색하여 가져옴
3. TCP/IP 방식으로 소켓을 통해 서버와 연결
4. 연결에 성공하면 웹 브라우저는 서버에게 웹 사이트의 사본을 보내달라는 HTTP 요청 전송
5. 서버는 요청에 맞는 HTTP 응답을 클라이언트에게 전송
6. 서버는 웹 사이트의 파일을 패킷 단위로 나누어 웹 브라우저에 전송
7. 웹 브라우저는 서버로부터 받은 패킷을 웹 페이지 데이터로 변환
8. 렌더링 후 완전한 웹 사이트를 사용자에게 보여줌

## URI (Uniform Resource Identifier)
- 리소스에 접근할 수 있는 **유일한 식별자**
- 통신 방식, 도메인 주소, 포트, 경로·쿼리·프래그먼트까지 모두 포함
- **URL과 URN을 포함**

### Fragment
- '#' 기호와 문자열이 함께 연결됨
- 해당 문서 내에서 '#' 뒤의 문자열이 id로 정의된 곳으로 바로 이동 (**앵커**)

### URL (Uniform Resource Locator)
- 리소스를 **위치**로 식별
- 리소스의 위치만을 나타내므로 프래그먼트는 URL에 포함되지 않음
- HTTP 프로토콜의 경우 http://[host]:[port]/[path]?[searchpart] 의 형식을 가짐

### URN (Uniform Resource Name)
- 리소스를 **이름**으로 식별
- 거의 사용하지 않음

## DNS (Domain Name System)
- 사람이 읽을 수 있는 **도메인 이름**을 컴퓨터가 이해할 수 있도록 **IP 주소로 변환**, 또는 그 반대로 변환해주는 분산형 데이터베이스 시스템

## IP 주소 (Internet Protocol Address)
- 네트워크 안에서 장치들이 **통신하기 위해 사용하는 번호**
- 모든 장치는 IP 주소를 가지고 있어야 함
- 사람이 IP 주소들을 일일이 외우기 어렵기 때문에 DNS를 이용하여 도메인 이름으로 바꿔줌

### IPv4
- 0~255 사이의 **10진수 4개**를 '**.**'로 연결한 형태의 주소 (**32비트**)
- 127.0.0.1 (localhost) 등 이미 예약된 특수한 주소가 있음
- 현재 가장 일반적으로 사용됨

### IPv6
- IPv4로 주소를 할당하기가 부족해져서 주소의 길이를 늘림
- 0~FF 사이의 **16진수 8개**를 '**:**'로 연결한 형태의 주소 (**128비트**)

## 포트 (PORT)
- 프로세스 또는 네트워크를 **식별하는 번호**
- 0 ~ 66535 사이의 **10진수 정수** (**16비트**)
- TCP일 때와 UDP일 때의 포트 번호가 다름
- 패킷의 IP 주소와 포트 번호를 소켓과 일치시켜서 패킷 전달

|포트 번호|내용|
|:---:|:---:|
|⋮|⋮|
|20|FTP (데이터)|
|21|FTP (제어)|
|22|SSH|
|23|TelNet|
|⋮|⋮|
|53|DNS|
|⋮|⋮|
|80|월드 와이드 웹 HTTP|
|⋮|⋮|
|119|NNTP|
|⋮|⋮|
|443|TLS/SSL 방식의 HTTP|
|⋮|⋮|

- 이외에도 다양한 포트 번호가 존재함

|포트 번호|내용|
|:---:|:---:|
|0 ~ 1023|잘 알려진 포트 (well-known port)|
|1024 ~ 49151|등록된 포트 (registered port)|
|49152 ~ 65535|동적 포트 (dynamic port)|

## 참고 사이트
- https://developer.mozilla.org/ko/docs/Learn/Getting_started_with_the_web/How_the_Web_works
- https://developer.mozilla.org/ko/docs/Glossary/URI
- https://en.wikipedia.org/wiki/Uniform_Resource_Identifier
- https://en.wikipedia.org/wiki/URI_fragment
- https://ko.wikipedia.org/wiki/URL
- https://ko.wikipedia.org/wiki/%EB%8F%84%EB%A9%94%EC%9D%B8_%EB%84%A4%EC%9E%84_%EC%8B%9C%EC%8A%A4%ED%85%9C
- https://ko.wikipedia.org/wiki/IP_%EC%A3%BC%EC%86%8C
- https://en.wikipedia.org/wiki/Port_(computer_networking)