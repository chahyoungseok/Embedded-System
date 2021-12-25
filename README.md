# Embedded-System 

<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#day-1">Day 1</a></li>
    <li><a href="#day-2">Day 2</a></li>
    <li><a href="#day-3">Day 3</a></li>
    <li><a href="#day-4">Day 4</a></li>
    <li><a href="#day-5">Day 5</a></li>
    <li><a href="#day-6">Day 6</a></li>
    <li><a href="#day-7">Day 7</a></li>
    <li><a href="#day-8">Day 8</a></li>
    <li><a href="#day-9">Day 9</a></li>
    <li><a href="#day-10">Day 10</a></li>
    <li><a href="#day-11">Day 11</a></li>
    <li><a href="#day-12">Day 12</a></li>
    <li><a href="#day-13">Day 13</a></li>
  </ol>
</details>



## Day 1

임베디드 시스템
 - 내장형 시스템
 - 특정기능
 - 제한적인 기능
 - 엄격한 제약사항(돈)
 - 실시간성을 요구
 - 신뢰성
 - 최적화 필요
 - 개발 환경의 이질성

OS
 - 하드웨어를 컨트롤, 관리하는 소프트웨어
<br><br>

### Computer System Organization

![7](https://user-images.githubusercontent.com/29851990/147375068-8cb0372e-a890-4f7d-b765-1f609c781441.PNG)

<br>
System bus : 시스템들을 연결하는 애들<br>
master : 통신을 주는 시스템<br>
slave : 통신을 받는 시스템(메모리는 보통 slave임)<br>
interrupt : 뭔가 오면 알림을 주면 그때수행
<br><br>


<br><br>
### Definition of Computer System Components

Hard real-time system
 - 잠깐 잘못돼도 큰일나는 것
 - ex) 원자로, 항공기류

Soft real-time system
 - Hard real-time system 보다는 괜찮은 것

<br><br>
### Computer System

Computer architecture
 - ISA + Memory model, register

Instruction Set Architecture(ISA)
 - 명령어를 기준세운 것

<br><br><br><br>
## Day 2

Symbolic Link  
 - 원본 파일의 이름을 가리키는 링크로 원본 파일이 삭제되면 사용 불가능하다.
 - 전혀 다른 파일이라도 가리키는 원본 파일 이름이 같으면 계속 사용 가능하다.

Hard Link
 - 원본 파일과 동일한 Inode 를 가지며 원본 파일이 삭제되더라도 링크 파일을 여전히 사용 가능하다.
 - 위치 정보를 가지고 있는 이름을 여러 개 생성하는 개념이다. 그렇기 때문에 한 파일을 지워도 하드에서 해당 위치를 찾아갈 수 있다.

절대경로
 - root에서부터 내 경로까지 쭉 나열한 것

상대경로
 - 지금 나를 기준으로 다른 파일을 찾는 것 

UserID
 - 유저 하나당 아이디가 부여된다

GroupID
 - 어떤 유저들이 속해있는 집단, 모든 유저는 반드시 하나이상의 그룹에 속해있어야한다.

Root
 - The userID is 0

Shell
 - 커널과 유저를 이어주는 인터페이스

<br><br><br><br>
## Day 3

Process
 - 객체와 같은 존재 / 동적이다

Program
 - 클래스와 같은 존재 / 정적이다

Multiprocessing
 - 프로세서를 여러개 두어서 수행시키는 것 -> 물리적으로 cpu가 여러개있다.

Multitasking
 - Time-Shared -> processing들이 동시에 수행되는 것처럼 보이게 하는 것

<br><br>
### Memory Layout
//사진
<br>
text (사이즈가 변하지않는다.)
 - 코드의 구조 ex) 명령어, 어셈블러, 기계어

data (사이즈가 변하지않는다.)
 - 원래필요한 변수, 전역변수, 정적변수 ex) static, 각종 상수

heap (사이즈가 유동적이다.)
 - 프로그램을 수행하면서 만들어지는 변수, 동적변수 ex) new, malloc...

stack (사이즈가 유동적이다.)
 - 함수호출 또는 일시적으로 생성되었다가 사라지는 파라미터, 매개변수, 리턴 벨류, 지역변수 등..

<br><br>
### Process States
//사진
<br>
New
 - 프로세스가 만들어질 때
Ready
 - 수행할 준비가 되어있지만 다른 프로세스가 cpu를 잡아먹기 때문에 기다리는 것

Waiting
 - 특정한 상황을 기다리고 있고, 입력이 되면 ready로 바뀐다.

Running
 - 프로세스가 동작하는 것

Terminated
 - 프로세스가 다 끝난상태

cf
 - ready, waiting 상태는 cpu를 먹고있는 상태가 아니다.

<br><br>
### PCB
//사진
<br>
process number
 - 프로세스를 가리키는 번호

register
 - 필요한 레지스터가 있으면 저장

list of open files
 - 프로세스에서 파일을 open하는데 그 리스트

<br><br>
### Process Scheduling
 - 하나의 프로세스가 cpu를 다 썻을 때, 다른 프로세스를 찾으러가는과정
 - 프로세스가 바뀔때 마다 Context Switch를 하게된다.

//사진

Context Switch는 Switch(interrupt, system call)를 하게 되면 실행하고있던 Process P0를 끝내는게 아니라 잠시 멈춘다.<br>
그러므로 P0가 쓰던 register 값(pc)을 저장을 하고, Process P1의 저장되었었던 state를 Load하는 과정이다.

Context Switch은 하드웨어 단에서는 꽤 시간이 걸리는 작업이다.<br>
그러므로 Context Switch을 자주하면 시간이 비례해서 걸린다.<br>
Time-Sharing을 사용하기 때문에 Context Switch을 하긴한다.<br>

그렇다고 Context Switch 하는 시간을 늘려버리면 cpu단에서는 눈에 보이지 않지만 I/O단에서는 엄청 답답해진다. (responsible)

따라서 Context Switch 시간이 적으면 프로세스가 전체를 수행하는 시간은 길어지지만 사용자와 인터페이스하는 것은 수월해진다.

<br><br>
### Operations on Processes
 - System은 프로세스를 생성하는 애 끝내는 애가 필요하다.
 - Kernel에서 사용자에게 프로세스를 어떻게 생성하고 끝내는지에 대한 함수를 제공해준다.
 - 모든 프로세스는 제일 처음 생성된 프로세스를 제외하곤 프로세스가 생성을 해야한다.
 - 모든 프로세스는 자신만의 아이디를 갖는다. (unique value)
 - Process Create Options

<br>

Process Create Options
  1. 생성하는 프로세스와 생성된 프로세스가 동시에 수행되게할지
  2. 부모 프로세스는 자식 프로세스가 끝날 때까지 기다리게 놔둘지
  3. 자식 프로세스가 만들어질 때 프로세스와 똑같은 메모리 상태
  4. 3과 다른 완전히 새로운 메모리로 프로세스 생성


<br><br>
### Process Creations

fork
 - 새로운 프로세스 생성
 - 새롭게 만들어진 자식 프로세스는 부모 프로세스와 똑같이 생성되므로 부모 프로세스가 수행하던 코드 그대로 수행을 진행한다. 그러므로 return된 pid를 보고, 위의 if에서 각자 갈길을 가게된다.
 - ex) pid (return value) = fork();

return value
 - 0 미만 : error
 - 0 동일 : 새로 생성된 자식 프로세스의 코드가 수행된다. 
 - 0 초과 : 부모 프로세스의 코드가 수행된다. 

exec
 - 프로세스는 프로세스가 생성해야한다. 근데 완전히 다른 일을 수행하는 프로세스를 만들고 싶을때는 exec()를 사용하여 이전 코드를 싹 없애면된다.
 - exec()를 수행하게 되면 앞서 보았던 heap, stack, data, text들이 cancel된다. 그리고 새로 Load한 코드를 수행한다.
 - 따라서 exec() 밑에 쓰는 것은 절대 수행되지 않는다. 하지만 OS단에서는 부모 프로세스와 자식 프로세스의 관계성은 남는다.


wait
 - 프로세스가 끝나면 Terminate 상태로 가도 잠시 대기한다.
 - 나를 생성했던 부모 프로세스가 내 상태를 확인할 때까지(자식 프로세스의 리턴 값), 대기한다.
 - 부모프로세스에서 wait()을 걸어으면, 계속 리턴값을 기다린다.

<br><br>

### Process Termination

프로세스를 이루는 가장 메인이 되는 함수에서 return 또는 exit()를 하면 프로세스가 종료된다.
종료할 때, 정수형 리턴 값을 가지고 있는 상태에서 끝이난다.

부모 프로세스에서 wait()를 안 넣어줘서 Terminated된 자식 프로세스가 wait()를 받지 못해 아무것도 수행하지 않는 “좀비 프로세스”가 만들어진다.

<br><br>
### Interprocess Coummunications

프로세스들끼리 데이터를 공유 해야될 수도 있다.<br>
하지만 프로세스들끼리는 메모리가 구분이 되어있다.<br>
공유할 수 있는 방법은 IPC이다.

IPC
 - Shared memory
   : 메모리공간을 공유해주는 방법
     - Kernel에 도움요청을 해야해서 제약사항이 많음.
 - Message passing
   : 일반적으로 많이 씀.
    - 특정 공간에 데이터를 쓴 다음 알람을 줘서 데이터가 필요한 	애들이 가져가는 방식 (보통은 계속 데이터를 기다리고 있다.)
    - 프로세스가 여러개 물렸을 때는 장점이다.

//사진

<br><br>
### Producer-Consumer

어떤 프로세스는 계속 데이터를 생성만하고, 어떤 프로세스는 데이터를 계속 가져다만 쓴다. 이것을 Producer-Consumer 관계 라고한다.

Producer가 아직 데이터 업데이틀 못했는데 Consumer가 데이터를 가져다 쓰면 작업이 망가진다. 따라서 이러한 구조일 때, 데이터가 업데이트가 되었는지 아닌지에 대한 체크를 하고 가져가야한다.

또는 Consumer가 바빠서 데이터를 못 가져간 경우 데이터 Queue는 한정적이므로 가져갔는지 확인후에 업데이트 해야함.



<br><br>
### Communication

Direct Communication
 - 특정한 애한테 걔만 보라고 명시적으로 찍어주는것
 - 링크가 자동적으로 생성이됨. (양방향이기 때문에)

inDirect Communication
 - Commuication box안에 넣어놓는다. (mailboxes라고 많이 부름)
 - 알람을 받은 애는 누가 쓴지는 모른다.

link 
 - unidirectional : 한쪽으로 링크연결
 - bi-directional : 양쪽으로 링크연결

<br><br>
### Synchronization

Blocking
 - 내가 데이터를 보내거나 받을 때, 상대방이 받았다고 말하기 전까지 또는 상대방에게 데이터를 받을 때까지 뒤의 코드를 수행하지 않는다.

Non-Blocking
 - 데이터를 상대방이 받던 말던, 상대방한테 데이터가 오던 말던 상관없이 진행한다.


<br><br>
### POSIX Shared Memory

shm_fd = shm_open(name, O_CREAT | O_RDWR, 0666);
ftruncate(shm_fd, 4096)

위의 코드를 실행하며 OS가 저 name으로 특정한 공간을 만들어놓는다.
그러면 프로세스들이 name을 알면 접근할 수 있어진다.

<br><br><br><br>
## Day 4

### Pipe

Ordinary pipes
 - 프로세스 생성할 때, 미리 꽂아 놓는 형식
 - Producer - Consumer구성에서 빈번하게 사용
 - unidirectional이다.
 - 보통 파이프를 uni로 2개 만들고, 그럼 양방향이 된다.

Named Pipe
 - Ordinary Pipe의 한계점은 부모자식관계가 아니면 쓸 수가 없다.
 - 범용적인 파이프가 필요해 만든 것이 Named Pipe
 - 하지만 현업에서는 오류도 많이 발생하여 잘 쓰지않는다.

<br><br>
### Communications in Clinent-Server

loopback 만드는 이유 : 인풋과 아웃풋을 분리하고, 인터페이스를 통일하고, 그 사이에 생기는 문제들은 커널에서 중재해주기 위해서
<br><br>

<br><br>
### 깜짝 문제

Questions : LINE A에서 출력되는 내용을 설명하라.<br>
Answer : 출력하는 부분은 부모프로세스에게만 있으므로 답은 5이다.
<br>
//사진

<br><br>

Questions : 최초의 부모 프로세스를 포함하여 사진에 표시된 프로그램에 의해 몇 개의 프로세스가 생성되는가?<br>
Answer : 한번 fork()를 하면 프로세스가 2개가 된다. 2^3 이므로 답은 8개이다.
<br>
//사진

<br><br>
### Thread

//사진
<br>

프로세스 내에서 자신만의 Content를 갖는 단위
하나의 프로세스는 하나이상의 Thread를 갖는다.

프로세스를 복사하면 저 위의 code, data, register etc.. 다 복사된다.
굳이 다 복사할 필요가 없어서 프로세스의 일정부분만 복사되도록 하는 별도의 Control 단위를 Thread라고 한다.

Thread는 복사될 때 PC, register, stack을 복사한다.
PC를 복사하므로 같은 프로그램 내에서도 각각 다른 위치를 동시에 수행할 수 있는 기능을 한다.

하나의 프로그램에 다수의 Thread는 code 공간을 공유한다. 따라서 하나의 Thread에서 문제가 발생하면 OS가 code공간에 할당된 resource를 회수하게 되므로 모든 Thread들이 멈추게 된다.

Benefits
 - 응답 속도가 빠르다.
 - 프로세스를 복사하는 것과 다르게 메모리공간을 덜 차지한다.
 - 만드는데 걸리는 시간도 적다.
 - Process보다 Thread가 Context Switching이 빠르다. -> 훨씬 더 멀티 테스킹에 적합하다.

<br><br>
### Multicore Programming

현대에 쓰는 컴퓨터나 핸드폰은 Multi Core이다.
Signal Core로 성능을 높이는데 한계가 있어서 Core 개수를 늘리자.

Concurrency : 하나의 Task가 끝나지 않았는데 다른 Task를 수행할 수 있는 성질

Parallelism : 코어가 여러 개 있어서 동시에 여러 Task를 수행하는 것.

<br>
Amdalhl's Law

//사진
<br>
p : 병렬화 할 수 있는 부분<br>
s : 코어의 개수

//사진

해당 그림과 같이 병렬화 할 수 없는 부분이 많다면 코어의 개수가 많아져도 성능향상이 더딜 수 밖에 없다.<br>
따라서 병렬화 할 수 있게 프로그램을 구성하는 것이 바람직하다.

Types of Parallelism
 - Data parallelism : 큰 데이터를 여러 코어들이 나눠서 계산하는 것.
 - Task parallelism : 데이터를 공유하고, 각각 하는 일들이 다르다.

<br><br>
### Pthread

Implicit Threading
 - 멀티 코어, 멀티 쓰레딩의 시대가 오면서 알아서 쓰레드를 코드레벨로 쓸 수 있게 만들었다.
 - 그치만 너무 외부에 노출시키지말고 내부에서 잘 처리하자.

Thread Pools
 - 쓰레드를 미리 만들어놓고 사용할 때 가져다 쓰고, 다 쓰면 가져다 놓는다. 그러면 생성시간을 단축한다.

<br><br><br><br>
## Day 5

### CPU Scheduling

어떠한 cpu가 어떤 프로세스를 쓸지 결정하는 것이 cpu Scheduling이다.

Cpu Burst 
 - 실제 프로세스가 cpu를 사용하는 시간

I/O Burst 
 - waiting하는 기간

ex)실제로 파일을 실행하는 시간은 Cpu Burst이고, cpu가 HDD에서 파일을 달라고 요청해서 HDD에서 cpu로 파일이 가는 시간은 I/O Burst가 된다.

<br><br>
### Clock Cycle

일정한 시간마다 하나하나의 계단식 블럭의 트리거 역할을 하는 소자를 clock이라고 부른다. (clock은 일정한 주기를 갖고 동작한다.)<br>
따라서 블럭안의 명령어는 clock에 동기화가 돼서 동작한다.<br>
주기하나당 명령어를 수행하므로 주기가 짧아지면 짧아질수록 성능이 좋아진다.<br>
clock cycle시간과 Frequency는 반비례다.<br>
따라서 Frequency가 높을수록 성능이 좋아진다.

Frequency 
 - 1초동안 clock이 얼마나 튕기나 (Hz라고 부른다.)

<br><br>
### CPU Scheduler

ready queue에 다수의 프로세스가 있다면 그것을 어떤 것 먼저 running state로 가져다 놓을 것이냐가 CPU Scheduler가 하는 일.<br>
CPU Scheduling이 동작하는 4가지
 1. running -> waiting
 2. running -> ready
 3. waiting -> ready
 4. Terminates

<br><br> 
### Preemptive Scheduling

Nonpreemtive
 - 한번 프로세스가 cpu를 장악하면 그 프로세스가 cpu를 안 쓴다는 신호를 보내기 전까지 아무도 cpu를 뺏어오지 못한다.
 - 뺏는 경우 : 스스로 놓거나 or 시간이 다 되었거나

Preemtive
 - 수행하는 중간에도 외부에서 강제로 ready queue로 보낼 수 있다. 

Dispatcher
 - Context Switing 할 때, 프로세스의 정보를 저장했다가 다른 프로세스 상태를 읽는 동작을 해주는 애
 - Context Switing을 너무 자주하면 프로세스가 실행하는 시간보다 Dispather가 수행하는 시간이 더 길어진다. 그것을 조절하는게 Dispatch latency이다. 

<br><br>
### Scheduling Criteria

Throughput
 - 전체 프로세스가 끝나는데 걸리는 시간

CPU utilization
 - CPU가 얼마나 놀지 않고 있었냐

Turnaround time
 - 각각의 프로세스들이 시작하면서부터 끝날 때까지 걸리는 시간의 평균

Response time
 - 사람과 상호작용을 안 해도 되는 일은 그냥 빨리 끝내기만하면 된다. 
 - 하지만 사람과 상호작용을 통해 해야하는일은 위의 것이 중요한 게 아니라 빨리 response를 주는 것이 더 중요하다.

waiting time 
 - 각 프로세스마다 평균 waiting time들 지표로 삼는 방법.

<br><br>
### Scheduling Methods

FCFS (First-Come, First-Served)
 - 먼저 온 애를 먼저 수행한다.
 - 이 방법에서 흔히 Convoy effect가 발생한다.
 - Convoy effect : 하나의 프로세스가 앞에서 막아버리면 뒤에 프로세스가 못하는 영향

SJF (Shortest-Job-First)
 - 제일 빨리 끝날만한(Burst time) 프로세스를 먼저 선택하는 것.
 - 과거의 일을 가지고 예측해서 Shortest-Job-Frist를 한다.
 - 실제로는 Burst time을 알 수 있는 방법을 몰라서 못 쓰는 방법이다.

SRTF (Shortest Remaining Time First)
 - Shortest-Job-Frist을 기본으로 하는데 Preemptive이므로 새로운 프로세스가 도착하면 끼어들 수 있다.

RR (Round Robin)
 - time slice와 Preemtive 성질이 있다.
 - 하나의 프로세스는 한 번에 일정한 시간이상(q)을 수행할 수 없다. 순서는 FCFS이다.
 - q가 작으면 작을수록 좋아 보이지만 context swithing의 overhead가 더 발생한다. (Dispatch latency)

Priority Scheduling
 - 프로세스의 우선순위를 우선으로한다.
 - Priority가 낮을수록 높은 것이다.
 - 현실적으로 많이 쓰인다.

<br><br>
### Starvation

Priority가 낮아서 영구로 돌아가는 프로세스 뒤로 걸려서 영구적으로 못 돌아가는 현상.<br>
보통 Round Robin과 Priority를 조합한다. -> 먼저 Priority를 수행하고 우선순위가 겹치면 Round Robin

Aging
 - Priority를 아무리 낮게 놔두더라도 일정 시간마다 Priority를 계속 올려줘서 Starvation을 해결함.

MultiLevel Queue
 - Ready Queue가 Priority 별로 따로 있어서 Queue 안에서는 Round Robin
 - 우선순위 : Real-time process -> kernel system process -> user interface process -> batch job process(user Disinteractive)
 - Multi Level Queue는 Aging 방법이 안 들어감.

<br><br>
### Approaches to Multiple-Process Scheduling

core가 n개가 있을 때, ready Queue를 공용으로 만들거나 개인용을 만드는 방법 2가지가 있다. (common ready / per-core run)<br>
Load balancing : per-core run queues에서 하나의 core가 다 일을 끝내면 다른 코어에 남아있는 일을 줘야함.

두 경우 모두 core와 프로세스간 선택에 있어서 고민할 것이 있다.

//사진
<br>
cpu와 메모리 사이에 데이터 이동은 컴퓨터 입장에서는 오래 걸리는 일이다. 그래서 찾은 방안이 조그맣지만 빠른 곳에 메모리공간을 둔다(Cache).<br>
 -> 많은 용량을 저장할 수 있는 공간은 싸지만 속도가 느리다.<br>
 -> 적은 용량을 저장할 수 있는 공간은 비싸지만 속도가 빠르다.

Context Switing Cost
 - Core가 하나의 Process를 처음 수행하면 Cache는 비어있다. 
 - 따라서 메모리에서는 자주 쓰이는 애들을 Cache에 채워놓는다. 
 - 그렇게되면 작업을 엄청 빠르게 수행하는데 Process가 바뀌게 되면 앞의 작업을 다해야하므로 속도가 느려진다.

위의 common ready는 Process하나 수행할 때마다 Context Switing Cost가 든다. per-core run과의 Load balancing을 비교를 해볼 수 있다.

<br><br>
### Simulaneous Multithreading

Process와 Process는 완전히 남남이지만, Process내의 Thread끼리는 많은 부분을 공유하므로 Context Switing Cost가 많이 줄어든다. 

S/W단에서 Multi Threading은 성능이 많이 좋아지지 않는다.<br>
SMT는 Multi Threading을 H/W 단에서 하는데 실제로 성능이 많이 좋아진다.

하나의 Thread가 I/O Burst나 다른 block에 걸렸을 때, 다른 Thread가 동작할 수 있게 H/W적으로 설계를 함

OS입장에서는 저렇게 구성하면 Thread를 core로 인식한다.<br>
-> 적어도 OS가 바라보는 입장에서는 멀티 스레딩과 멀티 코어는 같다.

하지만 멀티 스레딩이라해서 성능이 무조건 좋은 것은 아니고 block당하는 일이 없다면 싱글 스레딩을 하는 것과 같으므로 별로 이득이 없다.

<br><br>
### Real-Time CPU Scheduling

Soft
 - 전화같이 사람이 인식하는 수준의 딜레이가 있어도 되는 것.

Hard
 - 딜레이가 거의 있으면 안 되는 것.

Real-Time에서 말하는 필요한 시간
 - 이벤트가 발생한 시점부터 그 이벤트를 처리할 때 까지 걸리는 시간

Interrupt processing time
 - 이벤트가 발생했으면 cpu에게 알려주는 시간

Dispatch Latency
 - 중요한 프로세스가 떠서 cpu를 위임하는 과정 ---> 보통은 Hard와 Soft Real time에 영향을 많이 줌

real-time process execution
 - 실제로 어떤 일을 하는데 걸리는 시간

<br><br>
### File Information (Permission)

-/---/---/---<br>
1 : 파일 Type<br>
2~4 : 소유자(유저)<br>
5~7 : 그룹<br>
8~10 : 아무나<br>

r : 읽기권한<br>
w : 쓰기권한0<br>
x : 실행권한

<br><br><br><br>
## Day 6

### Race Condition

같은 데이터를 동시에 접근할 때는 막 허용하면 안된다.<br>
해결책은 동기화(Synchronization)이다.<br>
동기화 핵심 : 하나의 프로세스가 Shared Data를 조작하고 있을때는 다른애는 쓰면 안된다.

<br>

Producer - Consumer (Revisited)
 - 2개의 협업하는 프로세스가 있는데 하나는 생산만하고, 하나는 소비만하는 P-C관계가 있다. 
 - 그러려면 Buffer라는 공간이 있어야한다. Buffer의 크기는 지정이되는데 그러는순간 Buffer에 맞춰 제약된 데이터를 생산 소비해야한다.
 - Buffer에는 counter를 두어 제어할 수 있다.
 - 하지만 counter를 증가, 감소 시키는 과정에서도 위와같은 Data Inconsistency case가 나온다.
 - 따라서 공유하는 데이터가 있다면 Race Condition문제는 생긴다.



Kernel
 - 모든 프로세스가 접근한다. 
 - ex) fork를 할 때, Process ID를 받아오는데 이 ID의 저장소는 Kernel이다. 
 - 똑같은 Process ID를 가진 프로세스가 만들어질 수 도있다.

<br><br>
### Critical Section

Shared Data를 조작하는 영역을 Critical Section이라고 부른다.<br>
들어가는 부분 : entry section<br>
나오는 부분 : exit section<br>
entry section을 어떻게 만들어야 한 번에 하나의 프로세스만 들어갈 수 있냐?

<br>

Critical Section Problem
 - Mutual exclusion : 하나의 프로세스가 쓸때는 다른 프로세스는 사용 x
 - Progress : CS가 비어있는데 들어가고 싶은 프로세스가 있으면 반드시 그 중에 하나는 CS에 입장을 해야한다.
 - Bounded waiting : CS에 들어가려고 문을 두드리면 반드시 일정한 시간, 일정한 순서안에 여기에 입장한다. (우선순위를 빼앗겨서 Starvation문제가 발생하는 것을 막는다.)

<br><br>

//사진
<br>
Peterson's Solution
 - P0와 P1이 있을 때 저 flag와 turn을 공유한다.
 - turn은 누가 CS에 들어가게 할 것이냐에 대한 우선권을 주는 역할
 - flag는 나 CS 사용하고 싶다는 의견을 제시하는 역할
 - 본인 프로세스 입장에서 본인이 실행하는 것 : i
 - 본인 프로세스 입장에서 상대가 실행하는 것 : j

<br><br>

Peterson's이 제대로 된 해결책인지 아까 3가지의 문제를 가져와보자
 - Mutual exclusion : flag는 둘다 true가 될 수 있지만 turn은 0 아니면 1이다. 그러므로 둘중 하나는 수행이 된다.
 - Progress : CS가 비어있는데 사용하고 싶은 프로세스가 있다면 사용할 수 있냐에 대해서 사용을 하지않으면 flag를 내리기 때문에 사용하고 싶은 프로세스가 있다면 사용할 수 있다.
 - Bound waiting : turn = j처럼 왜 양보를 할까 => 두 프로세스간에 성능 차이가 많이 난다면 성능이 좋은 쪽만 수행하는 상황이 나올 수 있기 때문이다. 성능좋은 내가 상대방이 flag를 체크하기 전에 다시 flag를 바꿔버려서 CS를 수행한다. (Starvation 해결)

<br><br>

Out-of-order Execution
 - 리소스가 남는다는 가정하에 예전은 위의 예시처럼 상관없는 순서여도 먼저거를 안하면 뒤에것을 수행안했는데 요즘 컴퓨터는 상관없는 순서라면 먼저 수행한다.
 - 하지만 이 방식을 사용하게되면 순서가 바뀌어 다른 결과가 나올 수 있다는 문제가 생긴다.

Memory Barrier
 - memory_barrier()를 하면 그 위아래로는 코드를 교환하진 않는다. 그러면 어느정도 코드가 보장이 된다.

Atomic Instructions 
 - 내가 이 명령어를 수행할 때 다른 애들이 이명령어를 사용하지 못한다를 하드웨어단에서 보장한다.
 - ex) test-and-set, compare-and-swap
 - 성능저하가 심하다.

Mutex Locks
 - Synchronization을 위한 기능 
 - 이것은 보통 compare-and-swap으로 구현되고, 한줄 적으면 아까의 과정을 다 해준다. acquire lock, release lock

Semaphores
 - Mutex를 쓰면 하나만 접근 가능해서 내부에 리소스가 2개 이상 있을 때는 Semaphores를 사용한다.
 - Semaphores는 내부의 리소스를 카운팅해서 0이되면 못 들어가고, wait(), signal()로 아까의 알고리즘 기능을 수행한다.

spin lock
 - 모든 lock에서는 CS에 들어가지 못하면 무한루프가 도는데 이런 상황을 busy waiting이라고 부른다.
 - busy waiting 상태에서의 lock

Semaphore Implementation without busy waiting
 - 처음에 들어가서 lock을 못 잡으면 sleep을 한다. 그러면 cpu를 먹지 않는 wait queue에 들어가있는다.
 - 그리고 lock을 잡을 수 있는 상황이되면 다 쓴 사람이 wakeup을 호출하여 ready queue로 옮긴다. 
 - 근데 여기서 wakeup을 관련된 모든 사람에게 호출하므로 관련된 애들은 다시한번 잡아본다.
 - 따라서 내가 sleep 후 wakeup을 받았다고해서 무조건적으로 lock을 풀 수 있는 것은 아니다.
 - 여기서 또 문제는 sleep하고 wakeup을 하면 Context Switing을 하므로 단점도 있다.
 - CS를 기다리는 시간보다 Context Switing을 하는 시간이 길 경우 spinlock을 쓰는게 더욱 효율적이다.

Monitors
 - Synchronized를 쓰면 컴파일러나 OS가 알아서 CS에 2개가 못 들어가게 해놓는다.
 - 하지만 모든 구간을 Monitors을 하면 성능이 안 좋아진다.
 - 따라서 CS를 최대한 작게 하면서 문제가 없게 하는 것이 관건이다.

<br><br><br><br>
### Day 7

### Resource-allocation graph

//사진

네모가 리소스고, 동그라미가 스레드임<br>
리소스에서 스레드로 화살표 : 해당 리소스는 해당 스레드에 할당됬다.<br>
스레드에서 리소스로 화살표 : 해당 스레드는 해당 리소스가 필요하다.

<br><br>
### Necessary Conditions

deadlock은 아래 4가지조건이 만족해야 발생한다.
 - Mutual exclusion(상호배제) : 하나의 스레드가 어떤 리소스를 장악하면 다른 스레드는 그 리소스를 장악할 수 없다. 
 - Hold and wait : 내가 한번 리소스를 잡았으면 하던 일이 끝나기 전까진 안 놓고 다른 리소스를 잡을때까지 기다린다.
 - No preemption : 스레드가 어떤 리소스를 잡고있으면 다른 스레드는 뺏어갈 수 없다.
 - Circular wait(상호대기) : 내가 필요한 리소스는 상대가 갔고있는데 상대가 필요한 리소스는 나한테 있는 상황.

<br><br>
### Cycle

//사진

cycle인지 no cycle이냐도 구분을한다.<br>
예를들면 저 R3가 T1을 가르키면 cycle이 된다.<br>
no cycle이면 deadlock을 발생시키지 않고, 필요한 하나밖에 없는 리소스가 cycle에 포함되어있다면 deadlock이다.

<br><br>
### Deadlock Prevention

Deadlock이 걸리지 않게 하기위해 예방대책
 - Mutual exclusion, Hold and wait는 기존에 필요성을 보았을 때 함부로 없앨 수 없다.
 - No preemption 또한 기존에 필요성을 보았을 때 함부로 없앨 수 없다.
 - Circular wait는 구현방법도 어렵고 버든이 많이 존재한다.
 - 실제로 Deadlock Prevention은 구현 불가능하다.

<br><br>
### Deadlock Prevention
 - Thread가 내가 내일을 할 때 필요로 하는 최대의 리소스 개수(Maximum Needs)를 알고 있어야 한다는 전제조건이 있다.
 - ex) Banker's Algorithm
 - 하지만 Maximum Needs를 알고 있다는 가정이 불가능한 가정이다.

<br><br>
### Wait-for Graph
 - deadlock을 허용하고 deadlock 생기면 거기서 문제를 해결하려는 것 
 - 연관된 애들을 다 죽인다.
 - 하나씩 뺀다. (빼보면서 cycle이 없어지는지 아닌지를 본다.)
 - Deadlock이 걸리면 뭐 하나 죽여야되긴 하니까 문제를 최소화해서 Preempt해라

<br><br>
### Current OS

우리 다 같이 이 문제를 잊고 생기지 않다고 생각하자.
프로그래머가 잘 짜면 이런 문제 안 생겨 그러니 미루자!

괜찮은 방법이 많지만 성능을 너무 많이 떨어뜨리므로 구현 불가능하다.

<br><br><br><br>
## Day 8
