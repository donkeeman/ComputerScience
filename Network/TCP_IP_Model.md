# TCP/IP 모델

<table>
    <thead>
        <tr>
            <td align="center">TCP/IP 모델</td>
            <td align="center">OSI 모델</td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan="3" align="center">응용 계층</td>
            <td align="center">응용 계층</td>
        </tr>
        <tr>
            <td align="center">표현 계층</td>
        </tr>
        <tr>
            <td align="center">세션 계층</td>
        </tr>
        <tr>
            <td align="center">전송 계층</td>
            <td align="center">전송 계층</td>
        </tr>
        <tr>
            <td align="center">인터넷 계층</td>
            <td align="center">네트워크 계층</td>
        </tr>
        <tr>
            <td rowspan="2" align="center">네트워크 액세스 계층</td>
            <td align="center">데이터링크 계층</td>
        </tr>
        <tr>
            <td align="center">물리 계층</td>
        </tr>
    </tbody>
</table>

- OSI 모델 형식에 맞추어 TCP/IP 프로토콜을 **간략화**시킨 모델
- **4개**의 계층으로 구성
- OSI 모델 형식과 완벽히 일치하지는 않음

## OSI 모델과의 차이점
- OSI 모델에 비해 더 **안정적**
- **수평적** 접근 방식
- 계층 간의 경계가 **아주 엄격하진 않음**

## 네트워크 액세스 계층 (Network Access Layer)
- OSI 모델의 물리 계층 + 데이터링크 계층
- **물리적 장치** 간의 데이터 전송
- 장치의 **물리적 주소** 지정

## 인터넷 계층 (Internet Layer)
- OSI 모델의 네트워크 계층
- **논리적 주소 (IP)** 할당
- 목적지에 데이터를 보내는 **최적의 경로** 설정 (**라우팅**)
- IP (인터넷 프로토콜), ICMP (인터넷 제어 메시지 프로토콜), ARP (주소 확인 프로토콜) 등

## 전송 계층 (Transport Layer)
- OSI 모델의 전송 계층
- 네트워크를 통한 **데이터 전송**
- **네트워크 간** 통신의 흐름·오류 제어
- TCP (전송 제어 프로토콜), UDP (비연결 전송 프로토콜) 등

## 응용 계층 (Application Layer)
- OSI 모델의 세션 계층 + 표현 계층 + 응용 계층
- **통신 시작 및 종료** 기능
- 데이터의 **무결성**, **신뢰성** 검사
- **데이터 변환 및 캡슐화**
- **사용자**의 데이터와 직접 상호작용
- HTTP (HTML 문서 전송 프로토콜), NTP (네트워크 시간 프로토콜) 등

## 참고 사이트
- https://en.wikipedia.org/wiki/Internet_protocol_suite
- https://www.geeksforgeeks.org/tcp-ip-model/