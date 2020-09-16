# History of UNIX
* UNIX는 과거 비싼 라이센스였으며, 호환되는 무료 운영체제가 Linux
* MacOS도 UNIX를 뿌리로 하고 있다.

--------------------
## UNIX V6 Kernel?
* Memory resident part of UNIX
* 컴퓨터가 켜질 때, 커널은 메모리에 올라가서 상주하고 있음
* 대부분 C로 짜여져 있지만, 속도 최적화를 위해 일부(HW dependent, speed)는 어셈블리로 이루어져 있다.
* 그냥 a.out과 같은 실행 파일이다.
* consists of functions / 이를 system call function 이라고 부른다. (io, 메모리 할당, cpu 할당)
* 크게 3가지 부분으로 나누어짐
1. Process management
2. File System
3. I/O System

--------------------
## Hardware of Unix V6

> PDP-11(1970-1990s)
* 8KB page
* 256KB Memory

1. Instruction
2. Function
3. Process


1)Kernel(a.out) to be loaded into memory // 상주 \
2)User A Login -> shell a.out (first terminal on, process active, assing cpu, ...) \
3)User B Login -> shell a.out (second terminal on, ...) \
: (multi-user system)

shell -> creates a child process and wait

--------------------

## Multi-user system -- Protection

conflict process/memory/disk ... \
-> detect, recover ? \
-> No, we should prevent it (before happening)

Protection Between Process Domain{Memory, files, CRT, ...} \
shell -> must ask to kernal(system call) \
kernel -> after checks, allow resource \
CPU -> 강의 자료 참조(17 page)

I/O instruction은 kernel에서만 허용함 \
CPU는 현재 명령어가 kernel에서 요청한, 허가된 요청인지 판단할 기준이 필요함 \
-> 현재 프로세스가 user process 인지, kernel process인지 확인할 수 있어야함 \
-> mode bit가 존재함(14, 15번 bit of PSW) \
-> 해당 mode bit의 상태에 따라 user process인지, kernel process인지 확인할 수 있음

kernel instructions
- add/sub
- disk write
- disk read
- tape write
- disable interrupt
- enable interrupt

user instructions
- add/sub \
-> 자신의 process 내 메모리만

mode bit는 VM 등에서 활용됨
