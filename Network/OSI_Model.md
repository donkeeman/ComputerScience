
# OSI (Open Systems Interconnection) 모델

|층수|이름|데이터 단위|기능|프로토콜
|:---:|:---:|:---:|:---:|:---:|
7|응용 계층|데이터|사용자와의 상호 작용|HTTP, SMTP, FTP 등
6|표현 계층|데이터|데이터 변환|SSL, ASCII, MPEG 등
5|세션 계층|데이터|통신 연결 제어|NetBIOS, RPC 등
4|전송 계층|세그먼트 (TCP), 데이터그램 (UDP)|네트워크 간 데이터 전송|TCP, UDP 등
3|네트워크 계층|패킷|논리적 주소 할당|IP, IPSec 등
2|데이터링크 계층|프레임|네트워크 내 데이터 전송|Ethernet, MAC 등
1|물리 계층|비트|장치 간 데이터 전송|Wireless, RS-232 등

- **시스템 상호 연결**을 위해 ISO 표준의 공통 기반을 제공하는 **추상적** 모델
- **7개**의 계층으로 구성
- 특정한 곳에 이상이 생기면 해당하는 단계만 고칠 수 있음

## 1층 - 물리 계층 (Physical Layer)

- **물리적 장치** 간의 데이터 전송
- 데이터를 **비트 스트림**(0 or 1)으로 변환
- Wireless (무선 통신 프로토콜), RS-232 (시리얼 통신 프로토콜) 등
- 케이블, 리피터, 허브, 모뎀

## 2층 - 데이터링크 계층 (DataLink Layer)

- **동일한 네트워크**에 연결된(직접 연결된) 두 장치 간의 데이터 전송
- 받은 패킷을 **프레임**이라는 더 작은 단위로 쪼갬
- 물리 계층에서 발생할 수 있는 오류 감지 및 수정
- **네트워크 내** 통신 흐름·오류 제어 (양 쪽의 데이터 속도 조정 등)
- Ethernet (근거리 유선 네트워크 통신망), MAC (매체 접근 제어 프로토콜) 등
- 브리지, 스위치

### 매체 접근 제어 (MAC) 계층
- 장치가 매체에 대한 액세스 권한 및 데이터 전송 권한을 얻는 방법을 제어
- 장치의 물리적 주소 지정

### 논리 링크 제어 (LLC) 계층
- 네트워크 계층 프로토콜을 식별 및 캡슐화
- 프로토콜의 오류 검사
- 프레임 동기화 제어

## 3층 - 네트워크 계층 (Network Layer)
- **다른 네트워크**에 연결된 장치 간의 데이터 전송
(동일한 네트워크의 경우에는 네트워크 계층이 필요하지 않음)
- 받은 세그먼트를 **패킷**이라는 더 작은 단위로 쪼갬
- **논리적 주소 (IP)** 할당
- 목적지에 데이터를 보내는 **최적의 경로** 설정 (**라우팅**)
- 신뢰성이 무조건 보장되지는 않음
- IP (인터넷 프로토콜), IPSec (안전한 인터넷 프로토콜) 등
- 라우터, L3 스위치

## 4층 - 전송 계층 (Transport Layer)
- 네트워크를 통해 출발 호스트에서 도착 호스트까지 데이터 전송
- 최대 패킷 크기를 넘어서는 데이터는 **세그먼트**로 분할해서 전송
- **네트워크 간** 통신의 흐름·오류 제어
- 주어진 링크의 신뢰성을 제어하지만, 무조건 보장되지는 않음
- **OS**에서 관리
- TCP (전송 제어 프로토콜), UDP (비연결 전송 프로토콜) 등
- 게이트웨이

### 연결 지향 (Connection Oriented) 서비스
- 연결 설정 -> 데이터 전송 -> 연결 해제의 3단계 프로세스
- 장치 간의 연결을 위해 논리적 경로 할당
- 패킷 수신이 확인된 후 송신하므로 **안정적**, **신뢰성 보장**
- 여러 단계를 거치므로 통신 속도가 아주 빠르진 않음
- HTTP, TCP

### 비연결 (Connectionless) 서비스
- 데이터 전송의 1단계 프로세스
- 논리적 경로를 할당하지 않고 각각 독립 경로 사용
- 패킷 수신을 확인하지 않으므로 **신뢰성이 보장되지 않음**
- 하나의 단계만 거치므로 **통신 속도가 빠름**
- UDP, IP

### TCP (Transmission Control Protocol)
- 연결 지향 서비스
- 인터넷에서 기본값으로 사용됨
- 소켓 사용
- 서버-클라이언트 1:1 연결
- 패킷 전송을 위한 가상 회선 사용
- 데이터의 순서가 보장됨
- 3-way handshaking을 통하여 연결 설정, 4-way handshaking을 통하여 연결 해제
- 흐름 제어, 혼잡 제어
- 신뢰성 보장 -> **신뢰성이 중요한 경우 사용**
- 데이터가 손실된 경우 재요청을 하기 때문에 스트리밍 등 연속적인 전송이 필요한 서비스에는 부적합

#### 3-way handshaking
- 클라이언트 -- SYN (연결 요청) --> 서버
- 서버 -- SYN (연결 응답) 및 ACK (확인) --> 클라이언트
- 클라이언트 -- ACK (확인) --> 서버

#### 4-way handshaking
- 클라이언트 -- FIN (종료 요청) --> 서버
- 서버 -- ACK (확인) --> 클라이언트  
(서버 통신이 종료될 때까지 기다림)
- 서버 -- FIN (종료 응답) --> 클라이언트
- 클라이언트 -- ACK (확인) --> 서버  
(서버가 전송한 패킷이 뒤늦게 도착할 경우를 대비해 클라이언트는 일정 시간 동안 연결을 종료하지 않고 기다리다가 시간이 지나면 종료)

### UDP (User Datagram Protocol)
- 비연결 서비스
- 소켓 대신 IP 사용
- 서버-클라이언트 연결 시 1:1 뿐 아닌 다수:다수도 가능
- 데이터그램 (65536KB) 단위로 데이터 전송
- 데이터의 순서가 보장되지 않음
- 흐름 제어, 혼잡 제어를 하지 않음
- 속도가 빠름 -> **연속성이 중요한 경우 사용**
- 최소한의 오류만 검출하므로 이메일, 파일 전송 등 신뢰성이 보장되어야 하는 서비스에는 부적합

## 5층 - 세션 계층 (Session Layer)
- 로컬 응용 프로그램과 원격 응용 프로그램 간의 **통신 시작 및 종료** 기능
- 데이터 전송 시 특정 지점마다 **체크 포인트**를 지정하여 오류 식별 및 데이터 손실 방지
- NetBIOS (네트워크 기본 입·출력 프로토콜), RPC (Windows의 원격 프로시저 호출 프로토콜) 등

## 6층 - 표현 계층 (Presentation Layer)
- 응용 계층에 지정된 형식으로 **데이터 변환**
- 송·수신된 데이터를 **인코딩** 또는 **디코딩**
- 네트워크에서 전송하는 비트 수를 줄이기 위해 **데이터 압축**
- SSL (네트워크 레이어 암호화 프로토콜), ASCII (7비트 문자 인코딩 프로토콜), MPEG 등

## 7층 - 응용 계층 (Application Layer)
- **사용자**의 데이터와 직접 상호작용
- 네트워크로 전송되어야 하는 **데이터 생성**
- HTTP (HTML 문서 전송 프로토콜), SMTP (이메일 전송 프로토콜), FTP (파일 전송 프로토콜) 등

## 참고 사이트
- https://en.wikipedia.org/wiki/OSI_model
- https://www.cloudflare.com/ko-kr/learning/ddos/glossary/open-systems-interconnection-model-osi/
- https://www.geeksforgeeks.org/layers-of-osi-model/