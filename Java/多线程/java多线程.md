# java 线程池(Executors框架)

Executor 框架包括：线程池，Executor，Executors，ExecutorService，CompletionService，Future，Callable 等。

## 线程池
  
* newCachedThreadPool
  + 缓存型池子通常用于执行一些生存期很短的异步型任务 因此在一些面向连接的 daemon 型 SERVER 中用得多。但对于生存期短的异步任务，它是 Executor 的首选。
  + 能 reuse 的线程，必须是 timeout IDLE 内的池中线程，缺省 timeout 是 60s,超过这个 IDLE 时长，线 程实例将被终止及移出池。

* newFixedThreadPool 创建一个定长线程池，可控制线程最大并发数，超出的线程会在队列中等待。
  + newFixedThreadPool 与 cacheThreadPool 差不多，也是能 reuse 就用，但不能随时建新的线程。
  + 其独特之处:任意时间点，最多只能有固定数目的活动线程存在，此时如果有新的线程要建立，只能放在另外的队列中等待，直到当前的线程中某个线程终止直接被移出池子。
  + 和 cacheThreadPool 不同，FixedThreadPool 没有 IDLE 机制（可能也有，但既然文档没提，肯定非常长，类似依赖上层的 TCP 或 UDP IDLE 机制之类的），所以 FixedThreadPool 多数针对一些很稳定很固定的正规并发线程，多用于服务器。
  + 从方法的源代码看，cache池和fixed 池调用的是同一个底层 池，只不过参数不同:
    - fixed 池线程数固定，并且是0秒IDLE(无IDLE)
    - cache 池线程数支持 0-Integer.MAX_VALUE(显然完全没考虑主机的资源承受能力），60 秒 IDLE
  
* newScheduledThreadPool 创建一个定长线程池，支持定时及周期性任务执行。
  + 调度型线程池
  + 这个池子里的线程可以按 schedule 依次 delay 执行，或周期执行
  
* newSingleThreadExecutor 创建一个单线程化的线程池，它只会用唯一的工作线程来执行任务，保证所有任务按照指定顺序(FIFO, LIFO, 优先级)执行。
  + 单例线程，任意时间池中只能有一个线程
  + 用的是和 cache 池和 fixed 池相同的底层池，但线程数目是 1-1,0 秒 IDLE（无 IDLE）

## 任务

Runnable 不会返回结果，并且无法抛出经过检查的异常
Callable 有返回值 且call()方法只能通过ExecutorService 的 submit(Callable task) 方法来执行，并且返回一个 Future，是表示任务等待完成的 Future

## 自定义线程池

``` java
public ThreadPoolExecutor (int corePoolSize, int maximumPoolSize, long         keepAliveTime, TimeUnit unit,BlockingQueue<Runnable> workQueue)
```

* corePoolSize：线程池中所保存的核心线程数，包括空闲线程。
* maximumPoolSize：池中允许的最大线程数。
* keepAliveTime：线程池中的空闲线程所能持续的最长时间。
* unit：持续时间的单位。
* workQueue：任务执行前保存任务的队列，仅保存由 execute 方法提交的 Runnable 任务。

### 自定义线程池排队策略

* 直接提交。缓冲队列采用 SynchronousQueue，它将任务直接交给线程处理而不保持它们。如果不存在可用于立即运行任务的线程（即线程池中的线程都在工作），则试图把任务加入缓冲队列将会失败，因此会构造一个新的线程来处理新添加的任务，并将其加入到线程池中。直接提交通常要求无界 maximumPoolSizes（Integer.MAX_VALUE） 以避免拒绝新提交的任务。newCachedThreadPool 采用的便是这种策略。

* 无界队列。使用无界队列（典型的便是采用预定义容量的 LinkedBlockingQueue，理论上是该缓冲队列可以对无限多的任务排队）将导致在所有 corePoolSize 线程都工作的情况下将新任务加入到缓冲队列中。这样，创建的线程就不会超过 corePoolSize，也因此，maximumPoolSize 的值也就无效了。当每个任务完全独立于其他任务，即任务执行互不影响时，适合于使用无界队列。newFixedThreadPool采用的便是这种策略。

* 有界队列。当使用有限的 maximumPoolSizes 时，有界队列（一般缓冲队列使用 ArrayBlockingQueue，并制定队列的最大长度）有助于防止资源耗尽，但是可能较难调整和控制，队列大小和最大池大小需要相互折衷，需要设定合理的参数。
