# Procedure Call in Program Excecution

- 고급언어로 작성된 프로그램이 컴파일 되고 기계어로 바뀌고 실행되면 메모리에 각 실행파일의 주소공간이 할당된다.
- 이때 MIPS에서 주소공간은 논리적으로 낮은 0번지 부터 2^23-1까지 할당된다. 모든 프로그램마다 낮은 주소는 0번지 높은 주소는 2^32-1로 공간이 할당됨 이때는 실제 메모리의 물리적인 주소와 일치해서 생성되는 것이 아니기 때문에 논리적이라는 표현을 사용한것이다.

![image](https://user-images.githubusercontent.com/76929823/141066257-8052364b-ce14-48d1-aa53-78a8162cf3ec.png)

# What should be done with procedure call?

- 함수 호출이후에도 값이 유지되어야 하는 register 저장
  - 이때는 register 마다 함수호출하는쪽과 호출 당하는쪽이 처리해야할 register가 나누어져 있다.
- return address의 저장(보통 stack에 저장하지만 return address만 처리하는 register가 비어있다면 이곳에 저장)
- argument 저장
- 지역 변수를 위한 공간 할당 필요(stack에 할당)
  - 같은 함수가 여러번 호출 되면 지역변수는 매번 호출 됨
  - stack pointer($sp)레지스터가 stack의 가장 최근 저장 위치를 가리킴
  - hign address부터 쌓여서 점점 low address로 쌓여감

## MIPS의 STACK

    - STACK에 정보 저장
        - sub $sp, $sp, 4
            - 스택은 점점 낮은 주소 공간에 데이터를 쌓아가며 저장하기 때문에 현재 top위치에서 주소 4칸 이동하여(메모리는 byte당 하나의 주소를 갖고, 스택하나의 크기가 4byte이기 때문)
        - sw $t0, 0($sp)
    - Stack에서 정보 인출
        - lw $t0, 0(4sp)
        - add $sp, $sp, 4
            - 정보 다른 register로 옮기고 메모리주소 4칸 높은쪽으로 이동

## caller, callee와 jump & link

- 함수내에서 새로운 함수를 호출하면 return address를 저장하는 레지스터($ra)에 현재 $pc에 있는 값을 저장해두고 호출된 함수 위치로 jump & link
- 만약에 호출된 함수에서 다시 새로운 함수를 호출한다면 이때 $ra에 새로 돌아올 위치를 저장한다면 기존에 값이 사라지기 때문에 기존에 값은 현재 stack frame에 저장해둔다.

- register 저장에 대한 책임
  - callee
    - Saved s0 ~ s7 : 함수 호출이 되더라도 기본적으로 항상 저장되어야 하는 레지스터 이므로 호출하는쪽은 신경을 안쓰고 호출 당한함수 측에서 이 레지스터를 써야한다면 사용하되 자신이 저장해두고 return 할때 원상복구 해두어야함
    - $fp : 자기 자신의 fp로 설정하면서 원래 fp를 stack에 저장해둠
  - caller
    - Temporary t8, t9 : 임시 레지스터이기 때문에 지워질 가능성이 많으므로 호출하는 쪽이 저장해두어야함
    - argument $a0~$a3
    - Return value $v0~$v1
    - Return address $ra

## Stack Frame

- procedure가 사용 중인 데이터를 stack 상의 자신의 frame에 저장
- frame pointer($fp)를 각 함수의 stack frame의 시작 위치로 하여 procedure가 그 데이터를 접근
- stack fram에 저장되는 내용
  - 함수에 전달되는 인자 5번째 부터(4개까지는 $a0~a3에 저장)
  - svae된 register들의 값
  - 각 procedure의 local variables

## 함수 호출 과정 정리

![image](https://user-images.githubusercontent.com/76929823/141151314-2b47ad71-ce98-4bf9-9122-01706e674fd2.png)
