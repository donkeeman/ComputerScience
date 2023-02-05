# 쿠키 (Cookie)
- **키-값** 형태로 저장
- 쿠키 한 개당 최대 **4KB**까지 저장 가능
- 한 개의 도메인에 저장할 수 있는 쿠키의 개수가 **한정**되어 있음 (20개 권장, 브라우저마다 다름)
- 서버의 응답 중 `Set-Cookie` 헤더에 전달한 내용을 저장
- **세션 관리** (서버에 사용자의 정보 저장), **개인화** (사용자 맞춤 정보 제공), **트래킹** (사용자 정보 분석) 등을 위해 사용
- 사용자는 쿠키 전송을 **허용** 또는 **거부**할 수 있음
- 서버에서 정한 `expires` (**유효 날짜**) 또는 `max-age` (**만료 기간**) 동안 유지됨
- 유효 날짜 또는 만료 기간이 정해져 있지 않다면 **브라우저가 종료될 때 삭제됨**
- **브라우저** 또는 **자바스크립트** (`document.cookie`) 로 **접근**할 수 있음
- `httpOnly` 옵션을 이용하면 **자바스크립트로 접근 불가능** (처음부터 자바스크립트로 만들어진 쿠키는 `httpOnly` 가 먹히지 않음)
- `secure` 옵션을 이용하면 프로토콜이 **https**일 때만 쿠키 전송
- `samesite` 옵션을 이용하면 **외부 사이트**에서는 쿠키를 전송하지 않음
- 매번 자동 전송하므로 **서버**에 **부담**을 줄 수 있음

# 웹 스토리지 (Web Storage)
- **HTML5**에서 새롭게 등장
- **키-값** 형태로 저장
- 키, 값은 무조건 **문자열**이어야 함
- 데이터를 **서버로 전송하지 않음**
- **필요할 때**만 데이터를 꺼내 쓸 수 있음
- **클라이언트에서만 쓰이는 데이터**를 위해 사용
- 쿠키보다 최대 저장 용량이 큼 (보통 **5MB**, 브라우저마다 다름)
- **도메인이 다르면** (프로토콜, 호스트, 포트 번호 중 하나라도 다르면) 데이터에 **접근할 수 없음**

## 로컬 스토리지 (Local Storage)
- 저장된 데이터는 삭제하지 않는 이상 **새로고침**, **브라우저 종료 및 재시작** 시에도 **유지됨**
- 같은 URL이면 데이터를 **공유함**
- 브라우저 또는 자바스크립트 (`window.localStorage`) 로 접근할 수 있음

## 세션 스토리지 (Session Storage)
- 저장된 데이터는 **세션이 끝나면** (탭 또는 브라우저가 닫히면) **삭제됨**
- **새로고침** 시에는 데이터가 **유지됨**
- 같은 URL이라도 **다른 탭**이라면 데이터에 **접근할 수 없음**
- 같은 탭이어도 **도메인이 달라지면 새로운 세션 스토리지가 생성**됨
- **브라우저** 또는 **자바스크립트** (`window.sessionStorage`) 로 **접근**할 수 있음

## 참고 사이트
- https://developer.mozilla.org/ko/docs/Web/HTTP/Cookies
- https://ko.javascript.info/cookie
- https://developer.mozilla.org/ko/docs/Web/API/Web_Storage_API
- https://developer.mozilla.org/ko/docs/Web/API/Window/localStorage
- https://developer.mozilla.org/ko/docs/Web/API/Window/sessionStorage
- https://ko.javascript.info/localstorage