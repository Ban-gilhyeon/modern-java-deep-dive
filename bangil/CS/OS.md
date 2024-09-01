# OS

## 프로세스(Process)
```
컴퓨터 시스템에서 CPU 및 메모리를 이용하여 실행중인 작업
```
- 컴퓨터 시스템에서 실행되는 (거의) 모든 SW는 하나 이상의 프로세스를 이룸
- 프로세스는 생명주기(Lice Cycle)를 가지며, 이것은 운영체제가 관리 
- 프로그램 != 프로세스 
  - 프로그램은 실행이 준비된 SW 덩어리
  - 프로세스는 지금 실행하고 있는 SW의 생명체
=> 컴퓨터 구조에서 찾아보자 메모리 그거 

- 프로세스의 Life Cycle
  ![alt text](image-1.png)

## 스레드 (Thread)
 : `프로세스` 내에서 실행되는 여러 흐름의 단위 

 - single-threaded process
   - ![alt text](image-2.png)
 - multithreaded process
   - ![alt text](image-3.png)
 - 동시성(Concurrency)
   - ![alt text](image-4.png)
   - 동시성을 가지는 일들을 처리하는데 동기화(synchronization)가 필요
   - 위의 그림과 같이 Thread A와 Thread B가 동시에 실행될 때 어떤 Thread가 먼저 실행이 될 지는 OS가 정함 => 스케줄링

## 스케줄링(SCheduling)
스케줄링 문제 - 어느 순간 어느 작업을 수행할 것인지를 결정하는 문제 

- 효율성(Efficiency)과 공정성(Fairness) 사이의 이해득실 관계
  - 응답시간(reponse time)을 최소하
    - 각 작업이 도착했을 때로부터 완료된 떄까지의 시간이 중요
  - 시스템 처리울(Through put : 단위 시간당 처리한 작업량 )을 극대화
    - 문맥전환의 오버헤드를 고려하면 응답시간과 같은 기준이 아님
  - 공정성을 해치지 말 것 : 자칫 우선순위가 낮은 작업은 영원히 기다려(Starvation)할 수 있음 

### 스케줄링 알고리즘 

#### FCFS
First-come, First-served Scheduling 


| work | Time |
|------|------|
| p1   | 24   |
| p2   | 3    |
| p3   | 3    | 

- p1 -> p2 -> p3 이라고 가정하면 

    ![alt text](image-5.png)
 
  - 대기 시간 : p1 = 0, p2 = 24, p3 = 27
  - 평균 대기 시간 : (0 + 24 + 27) / 3 => 17
  - 평균 응답 시간 : (25 + 27 + 30) / 3 => 27
-  p2 -> p3 -> p1 이라고 가정하면
   -  ![alt text](image-6.png)
   -  대기 시간 : p1 = 6, p2 = 0, p3 = 3
   -  평균 대기 시간 : (6 + 0 + 3) / 3 => 3
   -  평균 응답 시간 : (3 + 6 + 30) / 3 => 13
  
### 최적성 보장 스케줄링 알고리즘

#### SJF(Shortest Job First)
- 지금 시작할 수 있는 작업들 중, 작업량이 가장 적은 것을 선택하여 스케줄 
- 비선점 방식

#### SRTF(Shortest Remaining Time First)
- 새로운 작업이 도착하고, 이것을 더 일찍 끝낼 수 있으면 -> 문맥전환(preemption)
- 매 순간, 남아 있는 작업량이 가장 적은 것을 선택하여 스케줄 

=> 평균 응답 시간 측면에서 최적의 알고리즘 
- 수학적으로 증명 됨
- 금방 끝낼 수 있을 작업을 우선 처리하므로, 직관적으로도 당연 
- 그러나 이 방법이 공정한가? (Starvation이 발생할 수 있음) -> 그렇기 떄문에 응답시간 뿐만 아니라 공정성도 고려를 해야 한다. 
