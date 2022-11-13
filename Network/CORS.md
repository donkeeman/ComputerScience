# CORS (Cross-Origin Resource Sharing)
- 현재 출처가 아닌 **다른 외부 출처**에 **리소스 접근 요청**을 보내기 위해 지켜야 하는 **브라우저 정책**
- **호스트**가 같아도 **프로토콜**이나 **포트**가 다르다면 다른 출처
- **브라우저-서버** 간의 전송 시의 **보안**을 위한 기능 (서버-서버 간의 전송은 해당 없음)
- 기본적으로는 **자격 증명 없이** 이루어짐
- 요청 시 `Origin` 헤더를 추가하여 전송
- 서버가 요청을 허용하면 응답에 `Access-Control-Allow-Origin` 헤더를 추가하여 전송
- 서버의 `Access-Control-Allow-Origin` 헤더의 값에 포함된 출처만 리소스 접근 요청이 허용되므로, 브라우저는 **자신의 출처가 헤더에 포함되는지** 검사
- 서버의 `Access-Control-Allow-Origin` 헤더의 값이 **와일드카드 (*)** 라면 **모든 출처**에서 오는 리소스 접근 요청을 허용하겠다는 의미

## 안전한 요청
- 데이터를 바꾸지 않는 **안전한 메서드**를 사용하는 경우
    - `GET`
    - `POST`
    - `HEAD`
- **안전한 헤더**를 사용하는 경우
    - `Accept`
    - `Accept-Language`
    - `Content-Language`
    - `Content-Type` 의 값이 `application/x-www-form-urlencoded`, `multipart/form-data`, `text/plain` 중 하나여야 함

### 단순 요청 (Simple Request)
- 안전한 요청 시, 프리플라이트를 생략하고 **바로 서버에 요청**을 보내는 것

## 안전하지 않은 요청
- 안전한 메서드를 사용하지 않거나, 표준 헤더를 사용하지 않는 경우
    - `PUT`
    - `PATCH`
    - `DELETE`
    - 그 외의 다른 HTTP 메서드들

### 프리플라이트 요청 (Preflight Request)
- 서버가 안전하지 않은 요청도 받을 수 있는지 확인하기 위해 미리 보내는 **예비 요청**
- `OPTIONS` 메서드 사용
- 서버는 **요청이 허용되는 메서드나 헤더 타입** 등을 응답
- 서버가 안전하지 않은 요청을 허용하지 않는다면, 브라우저는 본 요청을 보내지 않음

## 참고 사이트
- https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS
- https://ko.javascript.info/fetch-crossorigin
- https://ui.toast.com/weekly-pick/ko_20211110