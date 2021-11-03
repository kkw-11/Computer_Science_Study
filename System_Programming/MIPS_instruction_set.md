# MIPS Instruction Set Architecture

- Microprocessor without Interlocked Pipeline Stages
- IBM, 인텔 등 프로세서 마다 고유의 Instruction Set이 있지만 그 중에서도 MIPS Technologies에서 개발한 RISC 기반의 ISA를 말함
- 그 외에 또 많이 사용되는 RISC\*는 ARM
- MIPS에서 모든 기계어 instruction은 4bytes(32bits)

# MIPS에 포함되어 있는 Instruction

- 레지스터에만 접근

  - Arithmetic/Logic instructions
    - 산술논리연산을 수행하는 명령어이며, 레지스터에만 접근
  - Conditional branch instructions
  - Unconditional jump instructions
    - PC(program counter) 바꿔줌

- 메모리에만 접근
  - Data Transfer (Load/Store) instructions : 메모리에있는 데이터를 register로 load하는 등의 data transfer instructions을 수행하며, 속도가 느리다.

# MIPS register

- 정수형, 실수형 중 정수형 32개의 register, 4bytes의 구분을 위해 2^5 -> 5bits가 사용

## MIPS Memory

- 2^32 로 위치 지정 가능, 각각 byte 단위로 주소 지정, 총 2^32 bytes

### 용어

- 단위

  - bit : binary digit
  - byte : 1개의 영문자를 기억하는 최소 단위로 8bits
  - word : 컴퓨터 내부의 데이터 처리 및 전송의 단위이며, mips에서는 1word는 4bytes

- RISC는 적은 수의 컴퓨터 명령어를 수행하도록 설계된 마이크로프로세서
  - 프로그램에서 자주 사용되는 명령어만 효율적으로 구현하여 프로세서를 단순화해 H/W 구조가 단순
  - cf. CISC 는 복잡한 명령어를 수행하도록 설계된 마이크로세서: 많은 특수 명령어가 있어 일부는 거의 사용되지 않을 수 있고 H/W가 복잡하지만, 특정 명령에 최적화되어 설계되는 경우에는 RISC보다 속도가 더 빠르다


## Immediate addressing
- instruction 자체에 직접 포함되는 상수 필드
- 추가적 메모리 접근이 없어 빠른 연산 가능
- 단점: 재사용 불가, 32bit 내에 포함되므로 
