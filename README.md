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
    <li>Linux-mini-Shell(임베디드 프로젝트 링크) : https://github.com/chahyoungseok/Linux-mini-Shell</li>
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
![24](https://user-images.githubusercontent.com/29851990/147375297-3b19a4b9-222a-4a55-9eff-b505264a5242.PNG)
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
![28](https://user-images.githubusercontent.com/29851990/147375540-2ad0133e-e902-4285-b430-4bc6ee015246.PNG)
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
![26](https://user-images.githubusercontent.com/29851990/147375316-e3aab159-8160-4448-af89-737fcac0c153.png)
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

![27](https://user-images.githubusercontent.com/29851990/147375434-2116edfe-61b1-477f-b424-f25fcf6c465e.PNG)

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

![29](https://user-images.githubusercontent.com/29851990/147375564-81680b2f-0e45-463d-8cef-c566bc0d30cf.jpg)

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
![33](https://user-images.githubusercontent.com/29851990/147375569-7c76e614-08cc-416d-a989-70ebcce0a18d.PNG)

<br><br>

Questions : 최초의 부모 프로세스를 포함하여 사진에 표시된 프로그램에 의해 몇 개의 프로세스가 생성되는가?<br>
Answer : 한번 fork()를 하면 프로세스가 2개가 된다. 2^3 이므로 답은 8개이다.
<br>
![34](https://user-images.githubusercontent.com/29851990/147375570-f0659d7e-cf88-4a36-a963-0d06f5bfe42d.PNG)

<br><br>
### Thread

![30](https://user-images.githubusercontent.com/29851990/147375656-6803545e-1b04-4154-8f16-19bd87833b0a.PNG)
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

![37](https://user-images.githubusercontent.com/29851990/147375729-4df5aa24-9ea5-4282-a8eb-53405141b788.PNG)
<br>
p : 병렬화 할 수 있는 부분<br>
s : 코어의 개수

![38](https://user-images.githubusercontent.com/29851990/147375743-b93733d4-3c1f-48bc-99df-7fd9b7969377.png)

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

![23](https://user-images.githubusercontent.com/29851990/147375786-a5319cfb-61d0-4328-b062-008c21bf62a8.png)
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
2 to 4 : 소유자(유저)<br>
5 to 7 : 그룹<br>
8 to 10 : 아무나<br>

r : 읽기권한<br>
w : 쓰기권한<br>
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

![31](https://user-images.githubusercontent.com/29851990/147375817-5fd03307-47ff-4b7f-b577-d14873b874a0.PNG)
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

![32](https://user-images.githubusercontent.com/29851990/147375913-0ac4789f-ac83-4e82-8ac5-d033df615646.PNG)

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

![33](https://user-images.githubusercontent.com/29851990/147376013-e7efb873-3495-46ac-bc85-d951b6a5d5bb.PNG)

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

### File
 
 연관된 정보들의 집합을 만들고, 이름을 붙인 것<br>
 전원을 꺼도 여전히 저장이 되 있는 애들<br>
 더 작게 나눌 수 없는 저장단위
 모든 파일은 Directory안에 있어야한다.
 
 <br>
 
 File Open
  - Directroy를 뒤져서 파일이 어디있는지 찾아보고, 그에대한 정보를 메모리에 올리는 과정. (CPU는 모든 정보가 메모리에 있어야함.)
 
 <br>
 
 File Close
  - 메모리에 올라와있는 Content를 삭제 후 다시 Device에 저장하는 과정. (Read만 한거면 메모리에서 삭제를 안해도 된다.)

<br>

 File System
  - 스토리지에 있는 어떤 물리적인 내용을 우리가 보기좋게 논리적으로 바꿔주는 UI이다.
  - FCB를 통해서 전반적으로 파일시스템을 관리한다.
  - 실제로 어디에 써 이런 구체적인 명령은 Device driver가 한다.

<br>

 File System Layout
  - User 관리 : application programs
  - Kernel 관리 : logical file system | file organization module | basic file system  | I/O control
  - Device 관리 : devices

<br>

 application programs 
  - file open과 같은 c코드
 
 <br>
 
 logical file system 
  - directory operation을 통해서 directory를 뒤져 파일을 찾고, 그것을 FCB같은걸로 만들어서 메모리에 올려놓는다. 
  - 파일이있냐 없냐, 퍼미션이 뭐냐 등등 찾는다.

 <br>
 
 file organization module 
  - 찾는 파일의 이름과 meta-data등을 알았으면 그 logical한 정보, 블록들을 physical하게 바꿔주는 layer.
  - physical한 블록의 위치를 매핑해주는 테이블이 있다.

<br>

 basic file system 
  - 실제로 device에 몇 번 블록을 가져오라 하는 곳. 
  - logical한 몇 번째 블록은 사실 physical한 몇 번째 블록이라고 알려주고, 그러면 physical에 대응되는 블록의 정보를 불러오라고 Device driver에게 명령을한다.

<br>

<br><br>
### In-Memory File System Structures

System-wide open-file table
 - OS가 생각하기에 누군가 특정파일을 열었다면 그 정보가 메모리에 있어야한다 또는 저 파일을 접근하려면 어떤 FCB를 가지고 있어야된다 라는 정보를 가지고 있는 것.

<br>

Per-process open-file table 
 - 프로세스 입장에서 내가 파일을 열었다면 그 파일은 결국은 System-wide open-file table 어딘가에 있어야하므로 System-wide open-file table의 어떤 열린파일을 참조하고 있는지 가르키는 간접적인 포인터 테이블.

<br>

File System Usage
 1. System-wide open-file table를 뒤졌는데 내가 찾아야하는 File name이 있다면 수행하고있는 프로세스의 Per-process file entry를 찾은곳에 포인팅을 시켜놓는다.
 2. System-wide open-file table를 뒤졌는데 내가 찾아야하는 File name이 없다면 Directory Structure를 가서 저 파일을 뒤진 다음 FCB를 만들고, 그것을 메모리에 올리고, System-wide open-file table에 등록을 하고, 1의 과정을 수행한다. open file counter도 하나 증가한다.
 3. 파일을 닫으면 counter가 1 낮아지고, Per-process file entry가 사라지고, 링크도 끊어지고, counter가 0가되면 System-wide open-file table에서 방출이 된다.
 4. 사용하는 장점 : 속도의 문제

<br><br>
### Files allocations

Continuous allocations
 - 장점 : 간단하고, Directory도 시작과 끝 주소를 알면되므로 깔끔함.
 - 단점 : 연속적으로 저장해야하므로 연속된 빈공간을 찾아야한다.<br>데이터파일은 늘어나므로 낑겨놓으면 늘어날 수 없다.<br>외부단편화 : 블록이 5개가 들어가있는데 중간에 데이터가 들어가있어서 연속된건 못 들어가는 상황

<br>

LinkedList allocations
 - Linked List를 사용하면 외부단편화 문제는 해결된다.
 - 문제점 : 조금 커진다, 큰 리스트면 탐색하는데 시간이 너무 오래걸린다.

<br>

FAT allocations
 - 포인터들을 따로 테이블로 분리해놓은 것.
 - 이러면 FAT이라는 구조체만 사용하면 조금 빨라진다.
 - 문제점 : 테이블 공간이 만만치않음.

<br>

Indexed allocations method
 - 몇 번째 블록이 어디있는지에 대한 인덱스를 가지고 있다.
 - 5번 블록을 찾고 있다 -> 저걸 25번을 가면된다.
 - 문제점 : 하나의 블록안에 저장할 수 있는 인덱스의 개수 제한<br>블록을 실제데이터를 안쓰고 인덱스로 하나 쓴다는 점.

<br><br>
## Links(Hard, Symbolic)

HardLink
 - Directory는 단순 File만 가지고 있는 것이 아니라 File과 INode를 연결해주는 링크에 대한 정보도 가지고 있다.
 - Hard Link는 파일하나 당 하나만 만들 수 있지만 INode 입장에서는 개수제한이 없다.
 - 단순히 말해서 그냥 링크다. A를 통해 값을 바꿨다면 B를 통해 봐도 바뀌어있다.
 - Hard Link는 Link Count가 있고, unLink 기능도 있다.
 - 파일에 물려있는 Link가 하나도 없을 때 파일은 지워진다.

<br>

Symbolic Link
 - 윈도우의 바로가기처럼 폴더를 타고타고 들어가지 않아도 바로간다.
 - os는 신경안쓰고 우리끼리 정해놓는 개념
 - 이미 있는 링크를 가르키는 개념
 - 엄연히 다른 파일이기에 INode가 생김
 - INode가 가르키는게 file1이라고 가정할 때, file1이 없어지면 에러를 낸다.

<br>

copy와 HardLink 차이점 
 - Hard Link는 해당 INode에 링크를 하나 더 연결한 것이다.(링크가 걸려있는 다른 파일이 바꾸면 내 파일도 바뀜) 
 - copy는 파일과 Link와 INode까지 복사(복사 해온 파일이 어떻게되든 난 안 바뀐다)를 해온 것이다.
 - remove와 unlink의 차이도 위와 같다.


<br><br><br><br>
## Day 9

### Address Binding
MMU가 logical Address를 physical Address로 변환하는 것을 언제 변환하는지<br>
각각의 프로세스가 가지고 있는 Memory영역은 logical Address이다.

<br>

Types of Address Binding
 - Load time : 프로그램이 메모리에 위치된 곳을 기점으로 얼마만큼 떨어져있냐로 알려준다. (상대적으로 얼마나 벗어나 있는지)
 - ex) base + 0x~~

<br>

프로그램이 Load될 때 메모리주소를 준다고는 했지만 현실은 실제프로그램이 저 영역을 접근할 때, 즉 매번 명령어를 통해서 Translation할 때 마다 변환해서 준다. 이유는?
 - 프로그램은 시간에 따라서 HDD로 내려갔다가 올라오기도 하므로 주소는 계속 바뀐다. 그러므로 Loading time에는 결정할 수 없다.


<br>

relocation register
 - 프로그램을 메모리에 위치시킨 곳을 Base라고 하는데 (위의 ex참고) 그것을 결정시켜주는 애

<br><br>
### Dynamic Storage Allocation

메모리에 hole이 생길 때, 다음 process가 수행할 곳을 찾는 방법.

First fit
 - 발견한 memory hole중 가장 첫 번째로 발견한 hole에 넣는다.

Best-fit 
 - 모든 hole의 크기를 다 계산해서 집어넣는 process보다 크지만 그중에 가장 작은애한테 집어넣는방법.

Worst-ft 
 - 제일 빈공간이 큰곳에 집어넣는방법.

<br>

문제점 
 - External Fragmentation (외부 단편화) : 전체용량은 충분하지만 연속적인 공간이 부족하기 때문에 할당을 못하는 경우.

<br>

결론
 - 이론상으로도 실제 업무상으로도 Worst-fit이 External Fragmentation 문제를 줄인다.
 - 이런게 생기는 가장 근본적인 원인은 Contiguous Memory Allocation이다. 연속적으로 메모리를 할당하니까 저런문제가 안생길 수 가 없다.
 - Paging 기법 : 해결방안은 process를 잘라서 연속적이지 않게 잘라서 빈 공간에 채워 넣으면 된다. (잘린걸 Page라고 한다.)

<br>

### Paging

모든 프로그램을 같은 Page단위로 나눈다. (이제부터는 연속성이 의미가 없다.)<br>
page에서 Frame으로 넘어가도 page의 최소단위는 유지해서 메모리에 넣어주자.<br>
page table은 process마다 있어야한다.

<br>

page table 
 - 나눈 page들의 주소와 대응하는 Frame 주소를 써놓은 page table이 생긴다. 

page 
 - logical address에서의 관점

frame 
 - physical address에서 본 page (메모리 관점)

<br><br>
### Address Translation Scheme 
주소를 logical Address에서 physical Address로 변환해주는 개념.

<br>

offset 
 - page 시작주소로부터 해당명령어는 얼마나 떨어져있다를 나타내는 상대값

<br>

Address Translation Scheme을 할 때 page에 모든 것을 참여시키는게 아니라 page offset을 제외하고, logical address를 가르키는 주소같은 것만 Address Translation을 참여시킨다.<br>
2부분으로 나눠서 page offset은 그대로 전달을하고, 나머지 부분만 Translation을 해서 보낸다.

![1](https://user-images.githubusercontent.com/29851990/147377183-f25e5407-5f49-40b6-a135-95720df05b5e.PNG)

<br>

메모리가 딱 2bit만 저장할 수 있는데 그 메모리를 접근하기위해서 몇 bit 의 address bit이 있어야할까? 
 - 1bit만 있으면 된다. -> log2(n) bit만 있으면 된다.
 - 내가 address를 nbit를 구성해놓으면 메모리는 2의 n개만큼 구성해야한다.
 - 2의 10승 1Kbyte, 2의 20승 2Mbyte, 2의 30승 1Gbyte

page 4byte이고 physical memory가 32byte이므로 8frame 
logical memory는 16byte -> 실제 컴퓨터에는 32byte 메모리가 꽂혀있는데 프로그래머한테는 마치 프로세서 하나는 16byte까지만 쓸수 있다고 알려주는 것. (프로그래머 입장에서는 page가 4개)

<br>

![2](https://user-images.githubusercontent.com/29851990/147377341-c2f09554-63a5-4206-89a9-7c9f7c799229.PNG)
<br>
page table = {5, 6, 1, 2};

위의 그림에서 logical memory가 page table을 타고, physical memory로 가는거 직접해보자.<br>
page table을 타고 5번 Frame으로 가면 첫 번째 시작번지는 20이다.<br>
logical[0]의 physical address => 20<br>

저 그림에서의 page table에서 1:6을 1:0로 바꿔버렸다.<br>
그러면 logical memory에서 1번 page의 5번주소 f는 physical address의 몇 번째 주소로 옮겨지는가? 1번이다.<br>

ex) page가 4byte라면 이것을 표현하기 위해서는 2bit의 공간이 필요하다. 이 2bit를 page offset에 표현하고, page number는 그냥 쓰면 physical address에 계산할 때, Frame Number * 4 + page offset을 하면 된다.

문제점 
 - Paging을 써서 External Fragmentation은 해결 되었지만, Internal Fragmentation이 발생한다.
 - 내 프로그램이 4KB의 배수가 아니라면, 13KB짜리 프로그램을 만들면 실제 할당된 16KB에서 3KB를 날린다.
 - 또한, 대형 프로그램 같은 경우에는 page size는 커져야한다.

<br><br><br><br>
## Day 10

### Memory Protection

모든 프로세스는 자신만의 page table을 가져야한다. (프로세스마다 공유 x)<br>
CPU 입장에서는 page table은 그냥 하나의 메모리에 불과하다.<br>
그렇다면 page table은 어디에 저장이 될까? Page-table base register(PTBR) 에 있다. (하드웨어 레지스터)<br>
또한 수행되고있는 프로세스가 바뀌면 페이지 테이블도 바뀌어야 한다. ex) Context Switching

<br>

TLB
 - 순수 H/W인데 physical adddress를 찾는 과정이 생각보다 오래걸려서 만들었다.
 - 앞이 page number 뒤가 Frame number인 구조체를 만들어서 ~번 페이지는 프레임 ~번에있음 이렇게 H/W로 구현한다.
 - TLB에 가서 원하는 page number를 찾고 없다면 page table을 찾아간다.
 - Context Switching을 하면 TLB도 싹 다 비우고, 다시 채워야한다.
 - 따라서 TLB에 자주 쓰이는 page table의 정보를 가져다놓는다.
 - cpu입장에서는 TLB에 있는 정보를 가져오는 것이 훨씬 빠르다.
 - TLB에 내가 원하는 정보가 있으면 hit이고, TLB에 내가 원하는 정보가 없으면 miss이고, page table을 간다.
 - hope TLB hit rate : 99.n% 정도는 되어야 쓸만하다. (TLB hit와 page fault는 시간차이가 심하다.)
 - TLB miss가 나서 page table에서 정보를 찾으면 그 값을 가져와서 TLB에 저장한다.

<br>

TLB와 page table의 차이
 - page table은 모든 페이지에 대한 정보를 다 가지고 있어야한다.
 - TLB는 page table정도의 1/100, 1/1000 정도만 가지고 있어도 된다.
 - page table은 순서대로 n번째 entry를 찾아야하면 n번째로가서 frame을 찾으면된다.
 - TLB는 page number와 frame number가 둘 다 있어야한다.

<br>

Shared Pages
 - OS에서 이건 여러 프로세스가 공유할 수 있다고 선언해주면 공유시켜준다. 
 - virtual address입장에서는 내거를 쓰는 것 같지만 cpu입장에서는 메모리 한곳에있는걸 다 사용하는 것으로 보인다.
 - 원래는 서로 다른 프로세스의 page table에 같은 frame number가 있으면 안된다. 근데 Shared page를 통해서 가능하게 한다.
 - 다만, 읽기 전용이다.

<br><br>
### Demand Paging

필요한 page만 메모리에 올려주겠다.<br>
vaild-invaild bit에 v이면 메모리에 있으므로 유효하니까 찾아가는데, i이면 안찾아간다.<br>
내가 필요하지만 메모리에 없어 invaild여서 찾아가지 못하는 것을 page fault 라고 한다.<br>
MMU에서 Address translation할 때, page가 메모리에 없으면 "page fault"

<br>

Page fault
 - page fault가 발생하면 trap을 한다. (OS에게 알린다.)
 - OS는 그 page가 어디있는지 찾고, physical memory에서 새로운 page가 들어갈 비어있는 frame을 찾는다. 거기에 page를 load한다.
 - page table의 flag bit도 갱신해준다.
 - 이 과정에서 page를 들여보낼 때, 비어있는 frame이 없으면 누군가를 쫓아내야한다. 근데 그냥 버릴 수는 없고 어떡해해야할까? storage에 보낸다.

<br>

page out
 - 메모리에 있던 page가 storage에 가는 것.

page in 
 - storage에 있던 page가 메모리에 가는 것.

<br>

Copy on Write
 - fork()를 했을 때, 가상메모리 공간까지 복사가 되는데, 똑같은 부분이 존재하므로 그 부분을 공유하게 하면 좋다.
 - 하지만 공유하게 된다면 문제가 많아지는데, 임시로 공유메모리를 만들고, 만일 write를 하게 된다면 복사해서 하나 만든 뒤 그걸 토대로 page table을 다르게 가져가게 한다.

<br>

valid bit가 0인 애들은 왜 TLB에 존재할까?
 - Context Switching할 때, 4byte짜리 number들을 갈아치우는 것 보다 1bit짜리 valid bit을 0으로 만드는게 쉽다.

<br><br>
### Thrashing
 - OS는 프로그램을 10개 수행하면 동시에 시작시키지 않는다.
 - CPU의 utilization을 보고, 못한다 싶으면 어떠한 queue에 넣어놓는다.
 - 저 그래프의 x,y는 비례관계를 갖는다.
 - A,B의 중요 페이지 수가 4개라고 할 때, 총 올려놓을 수 있는 페이지 수를 6개라고 하자. A 혼자 올려놓고 쓰면 60%정도의 utilization이 나왔다고 하면 B가 들어오는 순간 B도 4개의 페이지를 올려놔야하므로 A가 차지하고있던 2개의 페이지공간을 줬다 뺐다 핑퐁을 치게된다.
 - 그러면서 계속 page fault가 나서 cpu의 utilization이 급격히 떨어진다. 그러면 os는 utilization이 떨어졌으므로 다른 C도 가져오면 utilization이 또 떨어지고, 악순환이 반복된다.

![35](https://user-images.githubusercontent.com/29851990/147377666-027a08ec-e64d-4a7c-8a50-19aa6b640abc.png)

<br><br>
### Page Replacement
 - victim : frame이 가득 차있어서 쫓겨나야되는 애
 - page replacement : 누굴 쫓아낼것이냐
 - 최대한 page fault가 적게 나오는 victim을 쫓아내야한다.
 - 아래는 victim을 정하는 알고리즘이다.

<br>

Optimal Algorithm
 - 가장 늦게 사용될 애를 쫓아내는 알고리즘

FIFO (First-In-First-Out)
 - 가장 오래된 애를 쫓아내는 알고리즘

LRU (Least Recently Used)
 - 가장 예전에 사용되었던 애를 쫓아내는 알고리즘
 - FIFO랑 다른점은 priority가 달라지는 것.

Belady's Anomaly
 - 줄줄이 miss가 발생하는 문제는 자주발생한다.
 - 프로그램은 무언가를 루프해서 돌기 때문에 “한번 수행된 애는 또 수행될 가능성이 높다” 라는걸 인지하고 만들어야한다.4
