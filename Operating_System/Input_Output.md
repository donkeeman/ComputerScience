# 입출력 (I/O)
- 사용자와 컴퓨터 사이의 통신
- 사용자 -- 입력 --> 컴퓨터
- 사용자 <-- 출력 -- 컴퓨터

## 입출력 장치
- 사용자로부터의 입력을 변환하여 컴퓨터에게 전달하거나, 컴퓨터의 응답을 사용자에게 출력하는 장치
### 입력 장치
- 키보드
- 마우스
- 마이크
### 출력 장치
- 디스플레이
- 스피커
- 프린터
### 입/출력 모두 가능한 장치
- 모뎀
- 네트워크 카드

## 표준 입출력
- 특별히 옵션을 지정하지 않았을 때 사용되는 기본 입출력
### 표준 입력 (stdin)
- 키보드를 이용하여 입력
### 표준 출력 (stdout)
- 디스플레이를 이용하여 결과 출력
### 표준 오류 출력 (stderr)
- 디스플레이를 이용하여 오류 출력
### 표준 보조 입출력 (stdaux)
- 통신 회선을 이용해 타 단말기와 입출력 통신
### 표준 프린터 출력 (stdprn)
- 프린터를 이용하여 출력

## 입출력 인터페이스
- 내부의 저장소와 외부의 입출력 장치 간에 정보를 전송하는 데에 사용하는 방식
### 프로그램된 I/O (Programmed I/O, PIO)
- CPU가 일정 시간마다 입출력 장치를 확인하면서 입출력이 있는지 **검사**하는 방식
- CPU와 입출력 장치의 **효율이 떨어짐**
### 인터럽트 구동 I/O (Interrupt-driven I/O)
- 입출력이 생기면 입출력 장치가 **인터럽트**를 이용하여 CPU에게 입출력이 생겼다고 알리는 방식
- CPU는 불필요한 검사를 하지 않고 필요할 때만 처리하므로 **효율 상승**
- 인터럽트가 두 개 이상 발생할 경우 **우선순위**를 결정하여 높은 것부터 처리
### 직접 메모리 접근 (Direct Memory Access, DMA)
- CPU를 거치지 않고 입출력 장치가 **직접 메모리에 접근**하는 방식
- DMA 동안에는 CPU가 버스를 제어할 수 없으며 **DMA 컨트롤러가 버스 제어**
- DMA 컨트롤러는 입출력 데이터를 메모리에 적재한 후 **인터럽트**로 CPU에게 알림
### I/O 채널 (I/O Channel)
- I/O 프로세서라고도 함
- 입출력 작업은 상대적으로 느려서 CPU에서 실행하면 그 동안 다른 작업을 실행하지 못하게 됨 (**I/O 바운드**)
- **입출력 작업만을 실행**하기 위한 장치
- 입출력 작업이 완료되거나 작업에 오류가 생기면 **인터럽트**를 통해 CPU와 통신
- 채널이 직접 메모리에 접근하는 경우도 있음
#### 셀렉터 채널 (Selector Channel)
- 한 번에 **한 장치**의 **고속** 전송
#### 멀티플렉서 채널 (Multiplexer Channel)
- 1Byte 단위로 입출력하는 **여러 장치**를 **동시** 관리
- 1Byte 단위라서 바이트 멀티플렉서 채널이라고도 함
#### 블록 멀티플렉서 채널 (Block Multiplexer Channel)
- 1Block 단위로 입출력하는 **여러 장치**의 **동시 고속** 명령 지원
### 메모리 맵 I/O (Memory-mapped I/O, MMIO)
- 메모리와 입출력을 **동일한 주소 공간**에 두어 접근
- 입출력 메모리와 레지스터를 **메모리의 일부로 취급**하므로 **같은 기계어 명령어**를 사용
- 구조가 복잡하지 않아서 **크기 및 비용 감소**
- 주소와 데이터 버스를 많이 사용하므로 **느림**
### 포트 맵 I/O (Port-mapped I/O, PMIO)
- 독립적 I/O (Isolated I/O) 또는 입출력 맵 I/O (I/O mapped I/O)라고도 함
- 메모리와 입출력의 **주소 공간을 분리**하여 접근
- **속도 및 효율 상승**
- 각각 **다른 기계어 명령어**를 사용해야 함

## 참고 사이트
- https://ko.wikipedia.org/wiki/%EC%9E%85%EC%B6%9C%EB%A0%A5
- https://en.wikipedia.org/wiki/Input/output
- https://en.wikipedia.org/wiki/Channel_I/O
- https://en.wikipedia.org/wiki/Memory-mapped_I/O
- https://en.wikipedia.org/wiki/Direct_memory_access
- https://www.geeksforgeeks.org/io-interface-interrupt-dma-mode/
- https://www.geeksforgeeks.org/memory-mapped-i-o-and-isolated-i-o/
- https://ko.wikipedia.org/wiki/%EC%9E%85%EC%B6%9C%EB%A0%A5_%EB%A7%B5_%EC%9E%85%EC%B6%9C%EB%A0%A5