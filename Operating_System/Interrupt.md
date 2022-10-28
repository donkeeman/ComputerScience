# 인터럽트 (Interrupt)
- 장치에서 **예외 사항**이 발생 시 CPU에게 알리는 행동
- 폴링 (Polling) 방식과 달리 CPU의 시간을 낭비하지 않고 효율적인 처리 가능
- **인터럽트 핸들러**를 이용하여 인터럽트 처리

## 인터럽트 핸들러 (Interrupt Handler)
- 인터럽트 서비스 루틴 (Interrupt Service Routine, ISR)이라고도 함
- 인터럽트를 처리하는 기계어 코드 집합
- 인터럽트의 종류에 따라 각각 다름

## 하드웨어 인터럽트
- 입출력 요청, 하드웨어 오류 등 **외부 하드웨어**에 의해 발생
- 전원 공급의 이상 등 **외부 요인**에 의해서도 발생
- 인터럽트 요청을 통해 인터럽트
- 소프트웨어 인터럽트보다 **우선순위가 낮음**
- 인터럽트 마스크 레지스터를 통해 인터럽트를 활성화/비활성화할 수 있음

### 마스크 가능 인터럽트 (Maskable Interrupt)
- 인터럽트 마스크의 영향으로 **비활성화 또는 무시**될 수 있는 인터럽트
- 우선순위 낮음
- CPU는 하던 작업을 끝내고 인터럽트 처리

### 마스크 불가능 인터럽트 (Non-maskable Interrupt)
- 인터럽트 마스크의 영향을 받지 않아 어떤 경우에도 **무시할 수 없는** 인터럽트
- 무조건 가장 **높은 우선순위**를 가지게 됨
- CPU는 하던 작업을 멈추고 상태를 저장한 다음 인터럽트를 처리하고 다시 돌아옴
- 치명적인 하드웨어 오류, 디버깅, 감시 타이머 등

### 가짜 인터럽트 (Spurious Interrupt)
- 어디에서 발생했는지 알 수 없는 인터럽트
- 유선 OR 회로 결함 등의 이유로 발생

## 소프트웨어 인터럽트
- 소프트웨어 실행 오류 등 **소프트웨어 내부**에서 발생
- 0으로 나누거나 지정된 메모리 영역 이외의 영역에 접근했을 때 등 **예외** 시에도 발생
- 시스템 검사 등 프로그램이 **의도적**으로 발생시키기도 함

## 인터럽트 트리거
- 인터럽트가 발생했다는 것을 CPU에 알리는 방법
### 레벨 트리거 (Level-triggered)
- 인터럽트 신호를 특정 활성 레벨에 맞게 구동
- 신호가 표시되면 인터럽트 요청을 인식
- 인터럽트가 끝나면 신호 무효화
- 인터럽트를 공유할 수 있음

### 엣지 트리거 (Edge-triggered)
- 인터럽트 신호의 레벨 전환 (상승->하강 또는 하강->상승)
- 펄스를 감지하면 인터럽트 요청을 인식
- 인터럽트가 끝나면 낮은 레벨을 유지
- 추가 인터럽트를 트리거하려면 높은 레벨로 돌아가야 함
- 인터럽트를 공유할 수 없음

## 참고 사이트
- https://ko.wikipedia.org/wiki/%EC%9D%B8%ED%84%B0%EB%9F%BD%ED%8A%B8
- https://en.wikipedia.org/wiki/Interrupt
- https://en.wikipedia.org/wiki/Interrupt_handler
- https://www.geeksforgeeks.org/difference-between-hardware-interrupt-and-software-interrupt/
- https://www.geeksforgeeks.org/difference-between-maskable-and-non-maskable-interrupt/