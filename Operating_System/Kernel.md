# 커널 (Kernel)
- 운영체제의 **핵심**
- 응용 프로그램 **실행에 필요한 서비스** 제공
- 하드웨어와 프로세스의 **보안 관리**
- 하드웨어에 직접 접근하는 대신 드라이버를 이용한 **하드웨어 추상화**
- 각 프로세스가 사용할 수 있는 **메모리의 양 결정** 및 사용 가능한 메모리가 충분하지 않을 때 수행할 작업을 결정
- **가상 메모리** 지원
- 입출력을 필요로 하는 응용 프로그램의 요청을 받고 **입출력 장치**를 사용하기 위한 편리한 방법을 제공
- 응용 프로그램이 운영체제에 접근할 수 있도록 **시스템 호출**

## 하드웨어 추상화
- 같은 종류의 장치에 대한 공통 명령어의 집합
- 운영체제의 복잡한 내부를 감추고 깔끔하고 일관성 있는 인터페이스를 하드웨어에 제공
- 개발자가 장치 독립적인 프로그램을 만들 수 있도록 함

## 모놀리식 커널 (Monolithic Kernel)
- 운영체제의 **모든 기능**들을 커널 공간에 적재 및 실행하는 기법
- 시스템 호출만으로 운영체제의 기능을 사용 가능
- 속도가 빠름
- 하나의 서비스에서 오류가 생기면 OS 전체가 실행되지 않음
- 사용자가 새 서비스를 추가하면 OS 전체를 수정해야 함
- 유닉스 계열의 운영체제에서 사용
- 현재는 모놀리식 커널에도 모듈 기능을 추가하는 경우가 많아짐

## 마이크로커널 (Microkernel)
- 운영체제의 기능 중 **최소한** (**프로세스 간 통신**, **메모리 관리**, **CPU 스케줄링**)만을 커널 공간에서 실행하고 나머지는 사용자 주소 공간에서 실행하는 기법
- 사용자 서비스에서 오류가 생겨도 커널 공간에는 영향을 끼치지 않으므로 유지보수에 용이함
- 사용자가 새 서비스를 추가하기 간편함
- 프로세스 관리가 복잡함
- 성능 오버헤드 존재
- 크기가 작아서 임베디드 시스템 등에 사용

## 하이브리드 커널 (Hybrid Kernel)
- 모놀리식 커널의 방식과 마이크로커널의 구조의 **혼합형**
- 운영체제의 거의 모든 기능들을 커널 공간에 적재
- 드라이버 테스트 시 재부팅할 필요가 없어짐
- 성능 오버헤드 감소

## 엑소커널 (Exokernel)
- 마이크로커널보다 **더욱 간소화**한 버전
- 자원 보호와 멀티플렉싱만 지원하여 크기가 작고 추상화 계층이 간단함
- 개발자들이 하드웨어와 관련하여 가능한 많은 결정권을 가지게 하기 위함
- 라이브러리 운영체제를 사용

## 참고 사이트
- https://en.wikipedia.org/wiki/Kernel_(operating_system)
- https://en.wikipedia.org/wiki/Monolithic_kernel
- https://en.wikipedia.org/wiki/Microkernel
- https://en.wikipedia.org/wiki/Hybrid_kernel
- https://www.geeksforgeeks.org/kernel-i-o-subsystem-in-operating-system/
- https://www.geeksforgeeks.org/microkernel-in-operating-systems/
- https://www.geeksforgeeks.org/monolithic-kernel-and-key-differences-from-microkernel/