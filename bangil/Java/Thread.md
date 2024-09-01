# Thread
- 동작하고 있는 프로그램을 프로세스라고 한다.
  보통 한개의 프로세스는 한 가지의 일을 하지만 스레드를 이용하면 프로세스 내에서 두가지 또는 그 이상의 일을 동시에 처리할 수 있다.

```java 
public class Sample extends Thread {
    public void run() {  // Thread 를 상속하면 run 메서드를 구현해야 한다.
        System.out.println("thread run.");
    }

    public static void main(String[] args) {
        Sample sample = new Sample();
        sample.start();  // start()로 쓰레드를 실행한다.
    }
}
```
Sample 클래스가 Thread 클래스 상속
Thread 클래스의 run메서드를 구현하면 sample.start() 메서드를 실행할 때 sample 객체의 run 메서드가 수행 됨
> Thread 클래스를 상속했기 때문에 start메서드 실행시 run메서드가 수행된다  
> Thread 클래스는 start메서드를 실행할 때 run메서드가 수행되도록 내부적으로 동작함


