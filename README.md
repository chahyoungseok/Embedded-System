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

![image](https://user-images.githubusercontent.com/29851990/147268871-dec6741d-c3ff-47d0-8b30-c7c7e50eaeb8.png)
<br>
System bus : 시스템들을 연결하는 애들<br>
master : 통신을 주는 시스템<br>
slave : 통신을 받는 시스템(메모리는 보통 slave임)<br>
interrupt : 뭔가 오면 알림을 주면 그때수행
<br><br>

![image](https://user-images.githubusercontent.com/29851990/147268894-fed0adea-105d-47aa-9296-d14d5f4c57b9.png)
<br>
Hard real-time system
 - 잠깐 잘못돼도 큰일나는 것
 - ex) 원자로, 항공기류

Soft real-time system
 - Hard real-time system 보다는 괜찮은 것
<br><br>

![image](https://user-images.githubusercontent.com/29851990/147268917-0f6c9712-095e-498f-998a-18a71bc31dc3.png)
<br>
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
![1](https://user-images.githubusercontent.com/29851990/147277591-dc6a3a67-b653-4599-8067-8e6515b04342.PNG)
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
![2](https://user-images.githubusercontent.com/29851990/147277602-4ef62842-e559-44ac-8f69-985500479d5f.PNG)
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
![image](https://user-images.githubusercontent.com/29851990/147269800-5a0b67c4-3aa3-4821-be3b-347543f6dafa.png)
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

![23](https://user-images.githubusercontent.com/29851990/147277928-29d02082-1f18-4dfd-8dc7-bf376b7111c8.PNG)

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

![image](https://user-images.githubusercontent.com/29851990/147269954-4e0fb04f-f308-44dc-a5e6-96d37f6c6a21.png)
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

![22](https://user-images.githubusercontent.com/29851990/147277975-a5c9308c-07ce-4c19-a3e1-ca89b6d081ee.PNG)

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
