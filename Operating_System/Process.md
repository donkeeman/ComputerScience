# 프로세스 (Process)
- 현재 **메모리** 상에서 실행 중인 **프로그램**
- **고유의 자원을 할당**받는 작업의 단위
- **하위 프로세스**를 가질 수 있음
- 상위 프로세스가 변경되어도 하위 프로세스에게 **영향을 끼치지 않음**
- 한 개 이상의 **스레드**를 보유하고 있음
- **스택**, **힙**, **데이터**, **코드**로 이루어져 있음
    |요소|설명|
    |:---:|:---:|
    |스택|함수 안에서 선언된 **지역 변수**, **매개변수**, **반환 값** 등과 함수 호출이 끝나고 **돌아갈 주소**를 저장 (**컴파일 시 크기 결정됨**)|
    |힙|`malloc()`, `calloc()` 등 **동적으로 할당되는 변수**를 저장 (**런타임 시 크기 결정됨**)|
    |데이터|**전역 변수**와 `static` **변수**를 저장 (**읽기, 쓰기 둘 다 가능**)|
    |코드|**코드**와 **매크로**를 저장 (**읽기 전용**)|

## 프로세서 (Processor)
- 프로그램을 실행하는 **하드웨어** 장치
- **CPU**, **마이크로프로세서** 등

## 프로세스 상태 (Process State)
- **New**, **Ready**, **Running**, **Waiting**, **Terminated** 의 상태를 가질 수 있음
    |상태|설명|
    |:---:|:---:|
    |New|프로세스가 처음 **생성**된 상태|
    |Ready|프로세스가 프로세서에 **할당되기를 기다리는** 상태|
    |Running|프로세스가 프로세서에 **할당**되어 **실행 중**인 상태|
    |Waiting|프로세스가 할당되어 있지만 사용자 입출력, 파일 입출력 등 **리소스를 기다리는** 상태|
    |Terminated|프로세스가 종료되어 메모리에서 **제거**되길 기다리는 상태|

### 프로세스 상태 전이 (Process State Transition)
![image](https://user-images.githubusercontent.com/79434205/218006488-4276c8c1-3cbe-4359-a319-791a114c12a5.png)
- 프로세스의 상태가 다른 상태로 변하는 것
    |상태|전이|설명|
    |:---:|:---:|:---:|
    |Admitted|New -> Ready|프로세스 생성 후 할당되기를 **기다림**|
    |Scheduler Dispatch|Ready -> Running|Running 상태인 다른 프로세스가 없다면 CPU를 **할당**|
    |Interrupt|Running -> Ready|우선 순위가 더 높은 프로세스가 Ready 상태가 되면 현재 실행 중인 프로세스를 **중단**|
    |Event Wait|Running -> Waiting|입출력 등의 **이벤트를 입력**받기 위해 Waiting 상태로 전환|
    |Event Completion|Waiting -> Ready|입출력 등의 **이벤트가 끝나면** Ready 상태로 전환|
    |Exit|Running -> Terminated|프로세스 실행이 끝나면 **종료**|

## 프로세스 제어 블록 (Process Control Block, PCB)
![image](https://user-images.githubusercontent.com/79434205/217978355-cc18f2e4-6a58-457d-ae7f-082dbc2fcc69.png)
- 운영 체제가 프로세스를 효율적으로 관리하기 위해 **프로세스에 관한 데이터를 저장**하는 자료 구조
- 프로세스가 중단되었을 때 현재까지의 진행 상황을 기억 -> 재실행 시 중단 시점부터 **이어서 실행**할 수 있음
- 프로세스 생성/제거 시 같이 생성/제거됨
    |구조|설명|
    |:---:|:---:|
    |Process State|프로세스의 **상태**를 나타냄|
    |Process Number|프로세스의 **고유 ID** (**PID**) 를 나타냄|
    |Program Counter|**다음 실행될 명령의 주소**를 나타내는 카운터|
    |Registers|누산기, 스택 포인터, 범용 레지스터 등 프로세스가 사용하는 **레지스터**들의 집합|
    |List of open files|프로세스를 실행하기 위해 열려 있는 **파일들의 목록**|
    |⋮|⋮|

## 프로세스 문맥 교환 (Process Context Switch)
- 현재 실행 중인 프로세스의 CPU 제어권이 다른 프로세스로 넘어가는 과정
- 하나의 CPU를 여러 작업이 **공유**할 수 있게 하기 위함
- 실행 중이던 프로세스의 데이터를 PCB에 저장하고 PCB에 저장되어 있던 다른 프로세스의 데이터를 불러와서 실행
- 문맥이 교환되는 동안 다른 작업을 할 수 없으므로, 문맥 교환이 자주 발생할수록 **오버헤드**가 발생하여 **CPU의 효율이 떨어짐**
- 메모리 주소도 교환하므로 캐시와 버퍼가 초기화됨
- 스레드 문맥 교환에 비해서는 **느리고 비용이 많이 듦**

## 프로세스 스케줄링 (Process Scheduling)
- 시스템의 여러 **자원**을 프로세스에게 **효율적으로 할당**하는 작업
- 문맥 교환 시 **스케줄링 알고리즘**을 통해 다음 프로세스를 선택
- 프로세스들은 준비 큐 (Ready Queue)에서 대기

### 선점형 스케줄링 (Preemptive Scheduling)
- 프로세스가 실행 중이더라도 **우선 순위**가 높은 다른 프로세스가 **CPU의 제어권을 가져갈 수 있음**
- **오버헤드**가 자주 발생

#### Round Robin (RR)
- 각 프로세스들은 **정해진 시간**만큼만 CPU의 제어권을 가질 수 있음
- 프로세스가 시간 내에 작업을 끝내지 못하면 준비 큐의 **맨 뒤**로 이동
- 준비 큐에 대기 중인 순서대로 모든 프로세스가 끝날 때까지 **순환**

#### Priority Scheduling (선점형)
- 프로세스가 실행 중이더라도 **우선 순위가 높은 프로세스**가 준비 큐에 들어오면 그 준비 큐를 선택
- **고정 우선 순위**의 경우 우선 순위가 한 번 정해지면 바뀌지 않으므로 구현이 **간단**하나 **효율이 떨어짐**
- **변동 우선 순위**의 경우 **효율적**이지만 우선 순위를 계속 계산해야 해서 **복잡**해짐

#### Shortest Remaining Time First (SRTF)
- 프로세스가 실행 중이더라도 **끝날 때까지의 시간이 가장 적게 남은 프로세스**가 준비 큐에 들어오면 그 프로세스를 선택
- 남은 시간이 적은 프로세스에 높은 우선 순위를 주는 것과 동일
- 남은 시간이 많은 프로세스는 계속 낮은 우선 순위만을 가지게 되므로 **기아 현상**이 발생할 수 있음
- 남은 시간을 계속 계산해야 함

#### Multi Level Queue Scheduling (MLQ)
- **준비 큐**를 여러 개로 **분리**하여 큐에 우선 순위를 부여하는 것
- 큐 안의 프로세스들은 선점형, 큐들끼리는 비선점형 방식을 사용함 (상위 큐의 작업이 모두 끝나야 다음 큐의 작업을 실행)
- 큐마다 다른 스케줄링 방식을 적용할 수 있음
- 프로세스는 다른 큐로 **이동할 수 없음**

#### Multilevel Feedback Queue Scheduling (MFQ)
- 준비 큐를 **최대 작업 시간**을 정하여 분리
- 프로세스의 작업 시간이 큐에서 정해진 시간보다 길면 다음 단계의 큐로 **이동**시킴
- 가장 마지막 큐는 FCFS 방식을 사용하며, 너무 오래 대기하면 상위 큐로 이동하게 되어 **기아 현상을 방지**
- 구현하기 복잡함

### 비선점형 스케줄링 (Non-preemptive Scheduling)
- 프로세스가 실행되는 동안은 다른 프로세스가 **CPU의 제어권을 가질 수 없음**
- 프로세스는 실행이 끝나서 스스로 반납할 때까지 **시간 제한 없이** CPU의 제어권을 가질 수 있음

#### First Come First Served (FCFS)
- 준비 큐에 대기 중인 **순서대로** 프로세스 실행
- 실행 중인 프로세스의 실행 시간이 아주 길다면, 대기 중인 다른 프로세스의 실행 시간이 짧거나 우선 순위가 높아도 **계속 기다려야 하는 문제점**이 있음

#### Priority Scheduling (비선점형)
- 준비 큐에 있는 프로세스 중 **우선 순위가 가장 높은 프로세스**를 큐의 맨 앞으로 보냄
- 고정 우선 순위의 경우 우선 순위가 한 번 정해지면 바뀌지 않으므로 구현이 **간단**하나 **효율이 떨어짐**
- 변동 우선 순위의 경우 **효율적**이지만 우선 순위를 계속 계산해야 해서 **복잡**해짐

#### Shortest Job First (SJF)
- 준비 큐에 있는 프로세스 중 **실행 시간이 가장 짧은 프로세스**를 큐의 맨 앞으로 보냄
- 실행 시간이 짧은 프로세스에 높은 우선 순위를 주는 것과 동일
- 실행 시간이 긴 프로세스는 계속 낮은 우선 순위만을 가지게 되므로 **기아 현상**이 발생할 수 있음

#### Highest Response-ratio Next (HRN)
- 준비 큐에 있는 프로세스 중 **응답 비율**이 가장 높은 프로세스를 큐의 맨 앞으로 보냄
- 응답 비율은 **실행 시간이 짧을수록**, **대기 시간이 길수록** 높음 ((실행 시간 + 대기 시간) / 실행 시간)
- 대기 시간이 길어지면 우선 순위가 높아지게 되므로 기아 현상을 방지

## 멀티 프로세싱 (Multi Processing)
- **두 개 이상의 프로세서**가 동시에 여러 작업을 **병렬**로 처리하는 것
- 한 프로세서에 문제가 생겨도 다른 프로세서에 영향을 끼치지 않음
- 프로세서끼리 주변 장치를 공유하므로 시간과 공간 비용을 줄일 수 있음

## 참고 사이트
- https://www.geeksforgeeks.org/difference-between-process-and-thread/
- https://www.w3schools.in/operating-system/process-management
- https://www.tutorialspoint.com/what-is-a-process-in-operating-system
- https://www.tutorialspoint.com/what-are-process-states
- https://www.geeksforgeeks.org/difference-between-thread-context-switch-and-process-context-switch/
- https://www.tutorialspoint.com/operating_system/os_process_scheduling.htm
- https://www.tutorialspoint.com/operating_system/os_process_scheduling_algorithms.htm
- https://www.geeksforgeeks.org/preemptive-and-non-preemptive-scheduling/
- https://www.geeksforgeeks.org/difference-between-multitasking-multithreading-and-multiprocessing/