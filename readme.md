## Operating System
---

> 사용자가 컴퓨터를 손쉽게 이용할 수 있도록 해 주는 프로그램으로서 하드웨어와 사용자의 가교 역할을 한다



### 기본 용어 정의


일괄 처리 : 다수의 프로그램을 읽어 저장해 놓되, 한 번에 한 개씩의 프로그램을 실행시켜 주는 방식

시스템 호출(System Call) : 유저 모드로 실행 중 커널 모드에서 해야 할 일이 생기면 프로그램은 시스템 호출을 하게 되고, 이후 그 일을 해 줄 운영체제 프로그램이 커널 모드에서 실행된 다음 다시 사용자 프로그램으로 복귀

부팅 : 커널이라고 불리는 운영체제의 일부가 메모리에 올라와 실행되어 장치들을 준비시키고 각종 레지스터 값을 초기화 한 뒤에 사용자의 입력을 받을 준비를 마친 상태

레지스터 : 메모리보다 빠른 기억 장치로, 주로 데이터나 명령어의 메모리 주소를 저장 및 계산하는 데 사용

인터럽트(Interrupt) : 각 자원들이 능동적으로 자신의 상태 변화를 CPU에게 알리는 방식 <-> 폴링(Polling)

폴링(Polling) : CPU가 주기적으로 각 자원들의 상태를 확인하는 방식

문맥교환(Context Switching) : 현재까지 하던 일에서 잠시 다른 일을 해야 할 때, 현재까지의 상태(PCB)를 보관해두었다가 다른 일을 한 뒤 다시 원래의 일을 함

프로세스 : 수행 중인 프로그램

프로세스 제어 블록(Process Control Block, PCB) : 프로세스가 생성되고 사라질 때 까지 필요한 정보를 담고 있으며 테이블 모양의 자료 구조를 띰

Swap : 프로세스가 메모리 공간을 뺏기고 디스크로 나가는 것(Swap out)과, 나중에 다시 메모리로 들어오는 것(Swap in)을 통칭해 Swap이라 함

스레드(Thread) : 프로세스의 실행 단위

다중 스레딩(Multi-threading) : 하나의 프로세스를 다수의 스레드로 만들어 실행하는 것

다중 프로그래밍 : 메모리에 여러개의 프로세스를 올려놓는 것

시분할 : CPU의 가동 시간을 적절히 나누는 것

스케쥴링 : 기다리고 있는 여러 프로세스 중 어떤 프로세스에 자원을 사용할 수 있도록 허가할지 결정하는 것

비선점 스케쥴링 : 한 프로세스가 CPU를 할당받았을 때 CPU를 스스로 반납할 때까지 계속 사용하도록 허용하는 방법

선점 스케쥴링 : CPU를 할당받아 실행 중인 프로세스로부터 CPU를 선점하여(빼앗아) 다른 프로세스에 할당하는 방식

병행 : 메모리에 다수의 프로세스가 같이 존재함

병렬 : 다중처리 시스템의 경우 여러 개의 프로세스가 동시에 시작될 때를 의미함. 처리기의 수가 하나 이상이여야 하며 기본적으로 병행성을 전제로 함

비동기적(Asynchronous) : 다른 프로세스들의 상태를 모른 채 실행되고 있음을 의미. 한 번에 한 프로세스만이 접근하도록 하고, 해당 자원에 대해 의도했던 실행을 완료하도록 보장 함

경쟁 상태(Race Condition) : 프로세스들이 공유 데이터에 대해 서로 접근을 시도하는 상황

상호 배제(Mutual Exclusion, Mutex) : 한 번에 하나의 프로세스만이 임계 영역에 들어가야 함

임계 영역(Critical Section) : 임계 자원에 대해 접근하고 실행하는 프로그램 내의 코드 부분

임계 자원(Critical Resource) : 두 개 이상의 프로세스가 동시에 사용할 수 없는 자원

라이브락(Livelock) : 두 프로세스의 속도가 교묘히 맞물렸을 때 둘 다 임계영역에 진입하지 못하는 현상

스핀락(Spinlock) : 베이커리 알고리즘 추가 설명 참조

동기화 : 임계영역에 대한 실행을 한 번에 한 프로세스만 차례대로 함

세마포어 : 세 개의 특수한 명령들만 접근할 수 있게 허용되는 보호된 변수로서, testAndSet이나 exchange 명령어보다 더 높은 수준에서 상호배제 명령을 구현하게 한다

모니터 : 공유 데이터들과 이들에 대한 임계영역들을 관리하는 소프트웨어 구성체

바쁜 대기 : = Spinlock

교착 상태 : 서로 다른 둘 이상의 프로세스가 상대 프로세스가 차지하고 있는 자원을 무한 대기하고 있는 상태

기아 상태 : 프로세스의 우선순위가 낮아서 원하는 자원을 할당 받지 못하는 상태

안전 상태(Safe State) : 시스템에 있는 모든 프로세스가 유한 시간 내에 정상적으로 종료될 수 있는 상태 <-> 불안전 상태(Unsafe State)

RAG(Resource Allocation Graph) : 자원 할당 그래프, 여러 자원을 그래프 자료 구조로 표현

Sink : 요청하는 자원이 없는, 즉 대기 상태가 아닌 활동 가능한 프로세스, Unblocked Process

검사점(Checkpoint) : 프로세스들은 실행의 중간 중간에 그 시점까지의 실행 결과를 보존하고 표시를 해두는데 이를 검사점이라고 함

오버레이(Overlay) : 메모리의 크기가 적재할 프로그램의 킉보다 크거나 같을 때, 프로그램의 일부만 먼저 적재한 뒤 샐행시킨 다음 나머지 부분을 다시 적재하여 실행을 이어가는 방식

내부 단편화 : 프로세스를 수용하고 남는 공간

외부 단편화 : 분할의 크기 자체가 워낙 작아서 프로세스들을 수용하지 못해 남는 공간

홀(Hole) : 외부 단편화로 남은 공간을 가르킴

50% 규칙 : 메모리의 빈 공간이 많음에도 불구하고 대두분이 홀이어서 별로 크지 않은 프로세스의 적재 요구조차 수용할 수 없는 상황이 생길 수 있게 되는 현상 -> 빈 공간 병합 (1. Adjacent Coalescing, 2. Compaction)

페이지(Page) : 모든 프로그램은 작은 조각들로 나눠지게 되는데, 조각들의 크기를 모두 같도록 할 때의 한 조각을 가르킴. 이는 전송 단위로서 블록(Block)이라고도 함 -> Paging

세그먼트(Segment) : 모든 프로그램은 작은 조각들로 나눠지게 되는데, 조각들의 크기를 서로 다르게 할 때의 한 조각을 가르킴. 이는 전송 단위로서 블록(Block)이라고도 함 -> Segmentation System

사상(Mapping) : 실행 중인 프로그램에서 참조하는 주소가 실제 메모리에 있는 주소와 달라서, 메모리상의 주소로 변환하는 것(프로그램에서 참조하는 주소 : 가상 주소, 실제 메모리상의 주소 : 실주소)

사상 테이블(Map Table) : 가상 주소를 실주소로 변환하기 위해 프로세스당 하나의 페이지 테이블을 만들어두는 것


### 배경 지식


프로그램이 CPU에 의해 실행되기 위해서는 반드시 주기억 장치(메모리)에 있어야 한다

프로세스의 상태 변화는 인터럽트에 의해 처리된다

스케쥴링 기준 : 1. 응답 속도, 2. 처리량 등등...지표들은 서로 상충되는 것들도 있기 때문에 특정 목적을 위해 스케쥴링을 하는 편인다

참고, 세마포어 뮤텍스 비교 {

###### 세마포어(Semaphore)

프로세스 간 동기화(프로세스 간 동기화 가능)

일정의 카운터라는 개념이 있어 주어진 수 만큼 자원에 접근이 가능

소유라는 개념이 없으므로 세마포어를 소유하지 않는 쓰레드도 해제 가능

###### 뮤텍스(Mutex)

쓰레드 간 동기화(하나의 프로세스 안에서 사용)

오직 하나의 대상만 자원에 접근이 가능(카운터가 1)(세마포어는 뮤텍스가 될 수 있지만, 뮤텍스는 세마포어가 될 수 없다)

소유라는 개념이 있어 뮤텍스를 소유하고 있는 쓰레드만이 해제할 수 있는 권한이 있음

}

무한 대기와 교착 상태 비교 : 무한 대기는 오랜 시간 후에라도(외부적 조치 없어도) 무한 대기로부터 벗어나 서비스를 받을 수 있지만, 교착 상태는 불가능하다


### 병행 프로세스와 동기화

> 프로세스들이 공유 데이터에 대해 서로 접근을 시도하는 상황을 경쟁 상태라 하며, 이러한 경쟁관계에 있는 프로세스들로 인해 상호배제, 교착 상태, 기아와 같은 문제가 발생한다

#### 상호 배제(Mutual Exclusion)

한 번에 하나의 프로세스만이 임계영역에 들어가기 위한 알고리즘

* Dekker Algorithm

```Java
While(true) {
  flag[i] = true;     // 프로세스 i가 임계영역 진입을 시도한다.
  while(flag[j]) {    // 프로세스 j가 현재 임계영역에 있는지 확인한다.
    if(turn == j) {     // 프로세스 j가 임계영역을 사용 중이라면
      flag[i] = false;    // 프로세스 i의 진입을 취소하고,  
      while (turn == j);  // turn이 j에서 바뀔 때 까지 기다린다...
      flag[i] = true;     // j의 turn이 아니면, 즉 임계영역에서 j가 나오면 재진입을 시도한다.
    }
  }
}
/*이 부분은 임계영역이다*/
...
turn = j;           // 임계영역의 사용이 끝나면, turn을 넘긴다
flag[i] = false;    // 진입 flag값을 false로 바꾸어 임계영역 사용 완료를 알린다.
...
}
```

* Peterson Algorithm

Peterson Algorithm은 Dekker Algorithm을 간결하게 만든 것으로, 상대방에게 진입기회를 양보한다는 차이가 있다

```Java
while(true) {
  flag[i] = true;            // 프로세스i가 임계영역에 진입을 시도
  turn = j;                  // 다른 프로세스에 진입 기회를 양보
  while(flag[i] && turn == j); // 다른 프로세스가 진입을 시도하면 대기 아니면 진입
/* 이곳은 임계영역이다. */
...
flag[i] = false;           // 임계영역 사용 완료
...
}
```

* Bakery Algorithm

위의 두 알고리즘과 달리 n개의 프로세스(혹은 스레드)에서 상호 배제를 구현하기 위한 알고리즘이다

```Java
while(true) {
...
  isReady[i] = true;                 // 번호표를 받을 준비
  number[i] = max(number[0 ~ n-1]) +1  // 현재 실행 중인 프로세스 중 가장 큰 번호로 배정
  isReady[i] = false;                // 번호표 수령 완료

  for( j =0; j < n; j++ ) {          // 모든 프로세스에 대해 번호표를 비교한다.
    while(isReady[j]);               // 비교할 프로세스가 번호표를 받을 때까지 대기
    while(number[j] != 0 && number[j] < number[i] && j < i);
// 프로세스 j가 번호표를 가지고 있고,
// 프로세스 j의 번호표가 프로세스i의 번호표보다 작거나 같을 경우
// j가 i보다 작다면(프로세스 j가 i보다 먼저 온 프로세스이면)
// 프로세스 j의 종료(number[j]=0)까지 대기
}
/* 이곳은 임계영역이다. */
...
number[i] = 0;                     // 임계영역 사용 완료. 차례를 기다리는 다른 프로세스들에게 임계영역의 진입 기회를 준다
...
}
```

위의 3가지 알고리즘은 운영체제의 특별한 지원 없이, 프로세스 간 협력을 통해 상호배제를 실현하는 것이므로 실행 시의 부하가 크며, 실수로 인한 오류의 가능성도 높다. 임계영역의 중복 진입을 막기 위해 while문을 계속 도는데 이것은 CPU를 가동하였으나 유용한 곳에 사용하지 못하고 낭비하는 결과를 초래한다(실제로는 아무일도 하지 않기보단 접근이 가능한지 무한 체크한다) - Spinlock


**** 아래는 하드웨어 기법 ****


* testAndSet 명령어

```Java
boolean testAndSet(boolean target) {
  boolean rv = target;
  target = true;
  return rv;
}

```

* exchange 명령어

```Java
void exchange(boolean r, boolean m) {
  boolean temp = r;
  r = m;
  m = temp;
}
```

위 두 명령어 기법은 바쁜 대기를 한다는 점과 기아를 겪을 수도 있다는 점, 또한 교착 상태에 빠질 우려도 있다

* Semaphore

```Java
static final int n = /* 프로세스 수 */;
semaphore s = 1;

P(S) {
  while (S <= 0); /* busy-wait */
  S--;
}
V(S) {
  S++;
}

static void p(int i) {
  while (true) {
    P(s);
    <critical section>;
    V(s);
    <remainder>;
  }
}

static void main() {
  parbegin
  p(1), p(2),...,p(n);
  parend
}

```

* 모니터

세마포보다 한 차원 높은 구조. 이유는 발생할 수 있는 오류를 줄일 수 있게 시스템에서 제공되는 언어 수준의 구조이기 때문

다시 공부...


### 메모리 관리

> 프로그램의 전부가 연속적으로 할당되는 경우

#### 고정 분할에서의 다중 프로그래밍

메모리를 여러 개의 분할로 나누어 놓고, 각 분할에는 하나의 프로세스만을 수용하도록 함으로써 다중 프로그래밍을 구현하는 방식

***단점***

1. 가장 큰 분할보다 더 큰 프로그램의 수용 문제 -> Overlay로 해결

2. 메모리 공간의 단편화 발생(내부 단편화, 외부 단편화)

#### 가변 분할에서의 다중 프로그래밍

분할의 시기와 개수 그리고 크기가 사전에 정해진 바 없이, 프로세스를 수용할 때 그 크기만큼 메모리 공간을 할당해 줌. 따라서 처음 메모리는 분할되지 않은 통째로 존재함

메모리의 빈 공간을 찾을 때 어떤 방식으로 찾을 것인가 ?

1. 최초적합(First-fit) : 요구되는 크기보다 큰 것 중 가장 먼저 발견되는 노드에서 할당. 어중간하게 빈 노드들이 많아진다

2. 최적적합(Best-fit) : free 리스트를 끝까지 탐색하고 요구되는 크기보다 더 큰 것 중 그 차이가 가장 작은 노드 할당. 시간 소모 있다

3. 최악적합(Worst-fit) : free 리스트를 끝까지 탐색하고 요구되는 크기보다 더 큰 것 중 그 차이가 가장 큰 노드 할당. 시간 소모 있다. 가장 비효율적


위의 3가지 가변 분할 방식으로의 관리는 오랜 시간이 지난 후 많은 Hole들을 발생시키고 이는 50% 규칙 현상으로 이어진다

버디시스템 : 최초에 큰 빈 공간의 메모리로 시작해 프로세스의 적재 요구가 있을 때 요구한 크기보다 크되, 차이가 가장 작게 나는 2의 승수 크기로 분할되어 할당. 이때 같은 크기로 분할된 인접 공간을 버디라고 한다. 이는 고정 분할과 가변 분할이 섞여 있는 분할 방식이다.

버디 찾는 방법 : 크기가 2^k이고 메모리의 시작주소가 x인 공간이 있을 때, 이 공간의 버디 주소는 x mod 2^(k + 1)의 결과 값이 0일 때는 x + 2^k, 2^k일 때는 x - 2^k가 됨


### 가상 메모리

> 프로그램의 일부를 비연속적으로 할당하는 경우 -> 프로그램 크기가 메모리보다 커도 된다
