# Instruction Set Architecture(ISA) 란?

- 비트로 이루어진 명령어 집합 구조  
- 하드웨어와 소프트웨어 사이의 interface에 대한 완전한 명세
- 타겟에 맞는 ISA에 따라서 HW/ SW를 만들게 됨



# system software

- 운영체제
- 넓은 의미로는 언어처리기(컴파일러, 어셈블리어), 유틸리티 프로그램 등 포함
- 응용프로그램의 요구에 따른 컴퓨터 하드웨어 자원의 제어 및 관리 담당
- machine dependent (특정 머신에서 돌아가는 기계어 - ISA, 의존적)

- cf. application : machine independent 


## 용어 정리 

### 운영체제(Operating System)란?
    - 시스템 자원(HW/ SW) 관리
### 컴파일러란?
    - 고급 언어로 작성된 프로그램 ISA에 맞게 변환
### 어셈블러란?
    - 기본 컴퓨터 명령어들을, 컴퓨터 프로세서가 기본 연산을 수행하는데 사용할 수 있는 비트 패턴으로 변환
### 링커란? 
    - 컴파일러가 만들어낸 하나 이상의 목적 파일을 가져와 이를 단일 실행 프로그램으로 병합
### 로더란?
    - 하드디스크와 같은 오프라인 저장 장치에 있는 특정 프로그램을 찾아서 주기억장치에 적재하고, 그 프로그램이 실행되도록 하는 역할


# ISA에 포함되지 않는 것?
- instructions의 수행 방법 ex. sequential, pipeline등 
- cache memory  (성능향상 목적)
- I/O device