# MIPS Instruction Set Architecture

- Microprocessor without Interlocked Pipeline Stages
- IBM, 인텔 등 프로세서 마다 고유의 Instruction Set 이 있지만 그 중에서도 MIPS Technologies에서 개발한 RISC 기반의 ISA를 말합니다.
- 그 외에 또 많이 사용되는 RISC\*는 ARM이 있습니다.
- MIPS에서 모든 기계어 instruction은 4bytes(32bits)입니다.

## MIPS에 포함되어 있는 것

- Instruction
  - _Arithmetic/Logic instructions_ : 산술논리연산을 수행하는 명령어이며, 레지스터에만 접근합니다.(핵심)
  - Data Transfer (Load/Store) instructions : 유일하게 메모리에 접근하는 명령어입니다. 메모리에있는 데이터를 register로 load하는 등의 data transfer instructions을 수행하며, 속도가 느립니다.
  - Conditional branch instructions : PC(program counter)를 바꿔주는 역할을 합니다.
  - Unconditional jump instructions : 위와 같이 PC를 바꿔주는 역할을 합니다. (함수 호출하거나, 조건문 반복문 등 수행 방법이 순차적이 아닐 때)
  - cf. [ISA에 포함되어 있지 않은 것](https://github.com/kkw-11/Computer_Science_Study/blob/master/System_Programming/about_ISA.md)
  
## MIPS register

- 정수형, 실수형 중 정수형 32개의 register, 4bytes의 구분을 위해 2^5 -> 5bits가 사용됩니다.

## MIPS Memory

- 2^32 로 위치 지정 가능인데, 각각 byte 단위로 주소 지정하니, 총 2^32 bytes 입니다.

### 용어

- bit : binary digit 입니다.
- byte : 1개의 영문자를 기억하는 최소 단위로 8bits와 같습니다.
- word : 컴퓨터 내부의 데이터 처리 및 전송의 단위이며, mips에서는 4bytes를 말합니다.

### RISC\* (Reduced Instruction Set Computer)

- RISC는 적은 수의 컴퓨터 명령어를 수행하도록 설계된 마이크로프로세서입니다.
- 프로그램에서 자주 사용되는 명령어만 효율적으로 구현하여 프로세서를 단순화해 H/W 구조가 단순합니다.
- cf. CISC 는 복잡한 명령어를 수행하도록 설계된 마이크로세서입니다. 많은 특수 명령어가 있어 일부는 거의 사용되지 않을 수 있습니다. H/W가 복잡하지만, 특정 명령에 최적화되어 설계되는 경우에는 RISC보다 속도가 더 빠릅니다. ↩
