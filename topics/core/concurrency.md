## Concurrency


### Resources

- [Concurrency in Practice by Brian Goetz](http://jcip.net) - Highly Recommended

### Table of Contents

- [Basics](#basics)
  * [Parallelism](#parallelism)
  * [Concurrency](#concurrency)
  * [Benefits of Threads](#benefits-of-threads)
  * [Thread safety](#thread-safety)
  * [Race Condition](#race-condition)
  * [Solutions to compound operations](#solutions-to-compound-operations)
  * [Synchronized](#synchronized)
  * [Liveness and Performance](#liveness-and-performance)
- [Sharing Objects](#sharing-objects)
  * [Data Visibility](#data-visibility)
  * [Safe construction](#safe-construction)
  * [Confinement](#confinement)
  * [Immutability](#immutability)
  * [Final Fields](#final-fields)
  * [Safe Publishing](#safe-publishing)
- [Composing Objects](#composing-objects)
  * [State Ownership](#state-ownership)
  * [Unmodifiable](#unmodifiable)
  * [Client-side locking](#client-side-locking)
- [Building Blocks](#building-blocks)
  * [Iterators and ConcurrentModificationException](#iterators-and-concurrentmodificationexception)
  * [Concurrent Collections](#concurrent-collections)
  * [InterruptedException](#interruptedexception)
  * [Synchronizers](#synchronizers)
- [Task Execution](#task-execution)
  * [Thread Pools](#thread-pools)
  * [Uncaught exception handlers](#uncaught-exception-handlers)
  * [Shutdown hooks](#shutdown-hooks)
  * [Daemon threads](#daemon-threads)
  * [Finalizers](#finalizers)
- [Applying Thread Pools](#applying-thread-pools)
  * [Thread pool sizes](#thread-pool-sizes)
  * [ThreadPoolExecutor](#threadpoolexecutor)
  * [Threads](#threads)
  * [Task Queues](#task-queues)
  * [Saturation Policy](#saturation-policy)
  * [Thread Factory](#thread-factory)
- [Avoiding Liveness Hazards](#avoiding-liveness-hazards)
  * [Deadlocks](#deadlocks)
  * [Starvation and LiveLock](#starvation-and-livelock)
- [Performance and Scalability](#performance-and-scalability)
  * [Costs on performance](#costs-on-performance)
  * [Steps](#steps)
- [Explicit Locks](#explicit-locks)
  * [Lock and ReentrantLock](#lock-and-reentrantlock)
  * [Advantages of lock classes](#advantages-of-lock-classes)
  * [Read-Write lock](#read-write-lock)
  * [Custom Synchronizer](#custom-synchronizer)


### Basics

#### Parallelism

- Tasks are divided into smaller sub-tasks that are processed simultaneously or parallel.
- Do lot of things simultaneously.
- It is achieved by through multiple central processing units(CPUs).
- Can’t be done by using a single processing unit.
- Improves the throughput and computational speed of the system.
- Deterministic control flow approach.
- Example - Processing Tax for differnt Users. Objects are not shared i.e user1, user2 etc
- Tools to enable parllelism - Thread, ThreadPool (ExecutorService, ForkAndJoin and Custom Thread Pools) 

#### Concurrency

- Task of running and managing the multiple computations at the same time.
- Achieved through the interleaving operation of processes on the central processing unit(CPU) or in other words by the context switching.
- Can be done by using a single processing unit.
- Increases the amount of work finished at a time.
- Deals lot of things simultaneously.
- Non-deterministic control flow approach.
- Example - Booking availale ticket. Shared object i.e availableTickets.
- Tools to deal with Concurrency - Locks/syncronized, atomic classes, concurrent data structures, computetableFuture,    synchronizers(CDL, Semaphore etc)


#### Benefits of Threads

- Exploiting multiple processors (Resource utilization) - Increasing core counts
- Simplicity of modeling applications - Distinct tasks can have own thread, and each can be written sequentially.
- Simplified handling of asynchronous events - If thread is blocked on IO, other threads  can still run. Though these days OS allow 100s of thousands of threads, so blocking is not a major issuer anymore. Thus NIO is not as crucial anymore (because its very complicated to implement).

Even if your class doesn't use threads, these do

- Underlying frameworks
- RMI
- JVM (for GC + Main)
- Timer
- Servlets &amp; JSP

#### Threads Creation

- A thread is a thread of execution in a program
- Threads with higher priority are executed in preference to threads with lower priority.
- Instances of class java.lang.Thread, or instances of subclasses of this class.
- Create Thread using Thread thread = new Thread(); and Start Thread using  thread.start();
- Threads can be created by extending the Thread Class or Implmenting Runnable interface in your class.

#### Sleep ()

-  Thread.sleep() is static method in thread class.
-  Keeps the lock or monitor even if thread is waiting
-  Sleep can be called without synchronized block.
-  Pause the current thread execution, relinquish(give up) the CPU and return it to thread scheduler.
-  native sleep(long millis) and  non native sleep(long millis,int nanos).
-  Throws Interrupted Exception if another thread interrupts a sleeping thread
-  Not finafinal
-  Purpose - If a thread does not want to perform any operation for a particular amount of time, then it goes for sleep()

#### Join ()

- Used to impose order on execution of multiple Threads.
- Throws IntrupptedException if another thread interrupted waiting for thread as a result of join() call
- Join is also a blocking method, which blocks until the thread on which join has called die or specified waiting time is over. 
- For example - t1 and t2 are two threads. t1.join is called in t2 then t1 will finish first followed by t2.
- Join is also an overloaded method in Java, three version of join() available
- Purpose - If a thread wants to wait until completing of some other thread then we should go for join().

#### Yield ()

- Thread.Yield() is static method and native too.
- Yield tells the currently executing thread to give a chance to the threads that have equal priority in the Thread Pool.
- Yield is not overloaded, non-final and dos not throw any exception.
- Purpose - If a thread wants to pass its execution to give chance to remaining threads of same priority then we should go for yield().

### Inter Thread Communication ( wait, notify and notifyall)
 - The current thread which invokes these final methods(part of Object class) on any object should have the object monitor else it throws   java.lang.IllegalMonitorStateException exception.
 - Wait tells the calling thread to give up the lock(releases the lock) and go to sleep until some other thread enters the same monitor and calls notify().
 - Wait is native call in java
 - Before calling wait() method, the	object should be synchronized, means the object should be inside synchronized block.
 - Notify wakes up one single thread that called wait() on the same object
 - Callling notify() does not actually give up a lock on a resource.
 - It tells a waiting thread that that thread can wake up. However, the lock is not actually given up until the notifier’s synchronized block has completed.
 - notifyAll  wakes up all the threads that called wait() on the same object. 
 - The highest priority thread will run first in most of the situation, though not guaranteed. 

#### Thread safety

Correctness means that a class _conforms to its specification_. A good specification defines _invariants_ constraining an object&#39;s state and _postconditions_ describing the effects of its operations.

_No set of operations performed sequentially or concurrently on instances of a thread-safe class can cause an instance to be in an invalid state._

#### Race Condition/ Data Race

- Race condition in Java occurs when Multiple thread access shared variable.Value of variable depends on the execution order (relative timing or interleaving) of threads.
- Occurs usually with _check-then-act_ (check stale value). Eg: Lazy initialization.
- Data races is different than race condition. Multiple thread access shared variable without synchronization. Atleast one thread is writing the vairable.


#### Solutions to compound operations

- Atomic classes (if only single variable is the issue)
- Synchronized (if multiple variables are to be updated atomically)

#### Synchronized

- Aka Intrinsic locks, Mutexes, monitors
- Are re-entrant means if a synchronized method calls another synchronized method which requires same lock then current thread which is holding lock can enter into that method without acquiring lock.
- Re-entrancy can help for overridden synchronized methods. Call to super.method() tries to re-acquire lock, and is permitted.
- no two threads can execute a synchronized method, which requires same lock, simultaneously or concurrently.
- synchronized keyword can be used only with methods and code blocks.
- Lock is released even if thread leaves synchronized method after completion or due to any Error or Exception.
- synchronization will throw NullPointerException if object used in synchronized block is null.
- both static synchronized and non static synchronized method can run simultaneously or concurrently because they lock on different object.
- you can not use synchronized keyword with constructor. It is illegal and result in compilation error.
- Do not synchronize on non final field on synchronized block in Java. because reference of non final field may change any time and then different thread might synchronizing on different objects i.e. no synchronization at all.
- Do not use String literals because they might be referenced else where in the application and can cause deadlock. String objects created with new keyword can be used safely. But as a best practice, create a new private scoped Object instance OR lock on the shared variable itself which we want to protect.
- [Do not synchronize on objects that may be reused](https://bit.ly/2T4ZZOr)


#### Liveness and Performance

- If scope of synchronized block is too large (say entire method of service). The whole performance benefit of multi-threading might be wiped off if service is accessed by lot of threads.
- Scope of synchronized block should be small enough that it covers all mutable state.

### Sharing Objects

#### Data Visibility

- When data is not synchronized, other thread might read stale data (due to caching of variables in CPU registers and L1, L2)
- 64-bit operations can be treated as 2 32-bit operations and leads to "word tearing", thus need to be synchronized. 
- Synchronized keyword ensures other thread reads latest data
- Volatile keyword does the same (flush and refresh)
- Semantics of volatile does not guarantee atomic increment!! Thus use volatile generally as status flags and such.
- AtomicLong and AtomicInt class should be used for counters and AtomicRefernce for caches, used by internal classes and non blocking algorthim.


Debugging tip: --server argument can hoist variables out of if condition (due to heavier optimization), while client JVM may not. Thus don&#39;t just think, if it works in client it works on server.

#### Safe construction

Do not let this reference escape the constructor. Even if it is last statement of constructor, the escaped reference of this, may not be pointing to completed object. (https://vlkan.com/blog/post/2014/02/14/java-safe-publication/)

Thus instead of constructors, listeners use setListener factory methods.

#### Confinement

Confining variables within method is best. For primitives its easy, but for objects, have to ensure its reference is not escaping. Thus Java has Collections.unmodifiableCollection and such.

Note: unmodifiableCollection doesn&#39;t allow references to be updated, but objects&#39; can still be updated if they are mutable.  Eg: Map&lt;String, Vehicle&gt;.. Vehicle object can still be updated.

ThreadLocal can also be used if its instance variable, but has to be thread-confined.

#### Immutability

Simple. Objects that cannot be modified, there are no threading issues.

#### Final Fields

Guarantee initialization safety.

```java
public Holder holder;

public void initialize() {
     holder = new Holder(42);   // not guarantee to be done atomically, unless variable is final
}
```

#### Safe Publishing

- Placing a key or value in a Hashtable, synchronizedMap, or Concurrent- Map safely publishes it to any thread that retrieves it from the Map (whether directly or via an iterator);
- Placing an element in a Vector, CopyOnWriteArrayList, CopyOnWriteArraySet, synchronizedList, or synchronizedSet safely publishes it to any thread that retrieves it from the collection;
- Placing an element on a BlockingQueue or a ConcurrentLinkedQueue safely publishes it to any thread that retrieves it from the queue.

Using a static initializer is often the easiest and safest way to publish objects that can be statically constructed:   _public static Holder holder = new Holder(42);_ 

### Composing Objects

Making a class thread-safe means ensuring that its invariants hold under concurrent access; this requires reasoning about its state. Objects and variables have a state space: the range of possible states they can take on. The smaller this state space, the easier it is to reason about. By using final fields wherever practical, you make it simpler to analyze the possible states an object can be in. (In the extreme case, immutable objects can only be in a single state.)

#### State Ownership

Owner of the state can help reason about the mutable access. In Java, there can be shared ownership or transferred ownership (since objects are passed as reference).


#### Unmodifiable

unmodifiableCollection doesn&#39;t allow references to be updated, but values themselves can still be updated if they are mutable.  Eg: Map&lt;String, Vehicle&gt;.. Vehicle object can still be updated.

locations = new ConcurrentHashMap&lt;String, Point&gt;(points);

unmodifiableMap = Collections.unmodifiableMap(locations);

unmodifiableMap stores &quot;live&quot; view of the locations map (i.e. any update to locations are reflected in unmodifiableMap).

To just give static view (non-live view) wrap it in new HashMap instance and then in unmodifiable.

Collections.unmodifiableMap(new HashMap&lt;String, Point&gt;(locations));}

#### Composition/Client-side locking

It can be difficult, because client has to lock on same object which the ThreadSafeClass uses. For example creating a putIfAbsent method in List class

- Cannot be achieved through having separate lock.
- Can be achieved using same lock as the list. But here locks are spreads over 2 classes (this and List)
- Best is to use composition, where you extend list, and ask clients to use this class.


### Building Blocks

#### Iterators and ConcurrentModificationException

Iterators are implemented by associating a modification count with the collection: if the modification count changes during iteration, hasNext or next throws ConcurrentModificationException. However, this check is done without synchronization, so there is a risk of seeing a stale value of the modification count and therefore that the iterator does not realize a modification has been made. This was a deliberate design tradeoff to reduce the performance impact of the concurrent modification detection code.

Easiest way to avoid this, is to hold lock on the list/collection during iteration (in client code). This will come at a cost of scalability. This again, can be avoided, by making copy of entire collection (by wrapping in a lock), and then without locking iterating over that cloned collection. But this comes with increased cost of memory &amp; speed (copying collection every time).

There are also hidden iterators, like when you do toString on collection it internally iterates over all elements appending to StringBuilder. In such cases, on client side use the Collection.synchronizedSet() and then perform all operations.

#### Concurrent Collections

**Java 5**

- ConcurrentHashMap instead of synchronizedMap (with operations put-if-absent, conditional remove, replace)
- CopyOnWriteArrayList instead of synchronizedList
- CopyOnWriteArraySet instead of synchronizedSet
- Queue &amp; BlockingQueue along with ConcurrentLinkedQueue
- PriorityQueue (non concurrent)

**Java 6**

- ConcurrentSkipListMap instead of synchronized TreeMap
- ConcurrentSkipListSet instead of synchronized TreeSet

**ConcurrentHashMap**

- Lock striping
- Concurrent readers and writers, thus high throughput
- Weakly consistent iterators instead of fail-fast
- Weakly consistent size and isEmpty too
- Cannot lock at client side using map object, because internally it uses different locks
- Due to above reason, we cannot exclusively lock map and thus cannot write our own put-if-absent
- Thus this map provides such operations put-if-absent, conditional remove, replace

**CopyOnWriteArrayList &amp; CopyOnWriteArraySet**

- Do not throw ConcurrentModificationException
- Copy underlying data during, modification
- No locking needed during iteration

**Other classes**

- ArrayBlockingQueue &amp; LinkedBlockingQueue
- SynchronousQueue
- ArrayDeque &amp; LinkedBlockingDeque (work stealing: each consumer has its own deque and it steals from other consumer&#39;s deque&#39;s tail if its own is empty)

#### InterruptedException

- Threads waiting in blocked state can be interrupted, using interrupt method. It has boolean flag for setting this.
- Good for cancelling long waiting tasks.
- If your code calls method which throws InterruptedException then:
- Choice 1 - Throw InterruptedException when called
- Choice 2 - Catch it, and restore the interrupted flag

#### Synchronizers

+ Latches
    - Can act as a gate, where all threads stop at the gate, and allowed once gate is opened.
    - This binary closed-open action is good for implementing &#39;Resource is initialized, now dependent actions can begin&#39;
    - Eg: Wait for all dependent services to init, wait for all players to arrive, wait until all worker threads finish etc.
    - CountDownLatch: await method, thread waits till count decrements to zero, or is interrupted or wait times out
    - FutureTask can also act as latch. future.get() method waits until task is completed and returns results.
    
+ Semaphores    
    - Permits (acquire and release)
    - Useful in creating bounded collections
    - Can instead use BlockingQueue, if resources themselves are to be tracked. Eg: Object pool

+ Barriers    
    - Similar to Latches with key difference
    - Latches are waiting for events, barriers are waiting for other threads
    - CyclicBarrier waits for fixed number of threads arrive at a point, repeatedly.
    - If all threads reach barrier point, barrier is passed and it resets.
    - await call returns arrival index to each thread, which can be used to &quot;elect&quot;
    - CyclicBarrier constructor accepts count (of threads) and Runnable (to run when threads reach this point).
    - Excellent for assigning sub-problems to threads and merging all results when barrier is reached.

+ Exchanger
    - Similar to Barrier that both wait until other arrives at same point.
    - Once reached they can exchange an object.
    - This is transfer of ownership of object (safe publication)
    - Example: Consumer exchanging an empty buffer with the producer, for a full buffer.

### Task Execution

#### Thread Pools

Threadpool with its bounded pool helps throttle the inputs/requests so as to not exhaust available resources.

Single Threaded Executors provide synchronization guarantee that writes made by a task will be visible to subsequent tasks.

**Types**

- newFixedSizeThreadPool - creates new thread, if one dies due to exception
- newCachedThreadPool - keeps increasing threads
- newSingleThreadExecutor - consumes task based on queue type (FIFO, LIFO, Priority etc), resurrects thread if dead
- newScheduledThreadPool - supports delayed and periodic execution similar to Timer

Usually shutdown call is immediately followed by awaitTermination.

#### Uncaught exception handlers

Thread provides facility for UncaughtExceptionHandler. When thread dies due to some exception, JVM checks if it has exception handler, if not it checks its ThreadGroup, if not then its super ThreadGroup and so on. Final system level ThreadGroup just prints stack trace to System.err

#### Shutdown hooks

- JVM also provides Runtime.addShutdownHook for when it attempts to shut down.
- Then it runs finalizers if runFinalizerOnExit is true
- It does not attempt to shutdown application threads, they die abruptly
- If these hooks do not complete, they hang the JVM. Thus do proper synchronization and not dead lock them.

#### Daemon threads

- Daemon threads do not stop JVM to shutdown
- GC, housekeeping threads are daemon threads
- Threads inherit daemon status of the owner thread
- When JVM halts, they do not call finally for daemon, nor cleanup their stacks, nor call finalizers.
- Thus better to use them sparingly

#### Finalizers

- Opportunity given by JVM to reclaim/free any resources being held up
- Not guaranteed to run
- Avoid as much as possible, catch-finally can more often do better job

### Applying Thread Pools

#### Thread pool sizes

- If its too big, it can exhaust memory (&amp; lot of overhead of creating/managing them)
- If its too small, not completely utilizing the CPU
- Usually, N (number of CPU cores) is right size of pools
- Though, if tasks do IO then, not all threads will be schedulable (tasks will be waiting for some resource), so its okay to increase size of threadpool.
- int N\_CPUS = Runtime.getRuntime().availableProcessors();
- Other deciding factors: memory, file handles, socket handles, and database connections

#### ThreadPoolExecutor

#### Threads
- newFixedThreadPool: corePoolSize == maximumPoolSize
- newCachedThreadPool: corePoolSize = 0 and maximumPoolSize = Integer.MAX\_VALUE
- Keep alive: how long to wait before unused thread is reclaimed (trade off)

#### Task Queues

- newFixedThreadPool and newSingleThreadedExecutor use unbounded LinkedBlockingQueue
- Try to use bounded (LinkedBlockingQueue, ArrayBlockingQueue or PriorityQueue)

#### Saturation Policy

- When bounded queue is full, what to do when task is submitted
- Abort - throw RejectedExecutionException
- Discard - discard silently
- Discard oldest - discards oldest from queue
- Caller Runs - return task to caller, so that caller thread can run it instead

#### Thread Factory

- Used to create new threads
- By default new non-daemon threads are created
- Can be overridden to create special threads which do say logging

### Avoiding Liveness Hazards

#### Deadlocks

- Database systems are great at handling deadlocks; they back-off certain transactions such that locks are released.
- JVM is not so kind. When threads are deadlocked, that&#39;s it, game over.

Transfer money is classic examples (with synchronized block on from and to accounts). If 2 calls are made, where 1st case arguments are from then to, and in 2nd case, its to then from. They may deadlock. To solve, either get comparable int keys or System.identityHashcode(), and order which account to be synchronized first. So no matter what&#39;s order of arguments, you always lock same account first, avoiding deadlock.

**How to avoid**

- Use only 1 locks (so no ordering issues)
- Order locks if multiple (ensure ordering is same no matter order of arguments)
- Use tryLock method of lock classes

#### Starvation and LiveLock

- Starvation is when thread is stuck
- Livelock is when thread keeps running (eg: message listener throws exception, rolls back then again tries processing of same object)

### Performance and Scalability

Amdhal&#39;s law - How much a  program can be theoretically sped up.

Trick is to divide into multiple tasks with their own data structures, and converge the results (this last step will be only step that will be sequential)

ConcurrentLinkedQueue is twice as fast as synchronizedLinkedList, because former has only final pointer updates as sequential while latter synchronizes on whole list.

#### Costs on performance

- Context switching
- Synchronization
- Data locality (memory cache)
- Blocking on locks

#### Steps

- Reduce lock contention
- Reduce scope - get in / get out
- Reduce lock granularity (too many times in and out is not good too)
- Lock striping
- Avoid hot fields
- Non blocking (compare-and-swap)
- Say no to object pooling - Java is super fast at new allocation, but getting objects from pool requires synchronization

### Explicit Locks

#### Lock and ReentrantLock

Lock implementations must provide the same memory-visibility semantics as intrinsic locks, but can differ in their locking semantics, scheduling algorithms, ordering guarantees, and performance characteristics.


#### Advantages of lock classes

- More flexible. Need not release lock in same block of code unlike synchronized
- &quot;Synchronized block&quot; threads cannot be interrupted while they are waiting for lock.
- lockInterruptibly can stop waiting for lock on interrupt
- Deadlock can be avoided by trying to acquire lock, and releasing already acquired, if cannot acquire new one.
- Intrinsic locks can&#39;t release locks on timeout
- Since Java 6, performance of intrinsic and reentrant lock is very similar. Earlier it used to be slower.

Always do lock.unlock in finally block

Locks can be fair/unfair. Fair locks implement queues to handle requests for a lock. Ofcourse, fairness comes with cost of performance.

#### Read-Write lock

- Allows multiple concurrent readers, but only single writer
- Great for data structure with lot of reads
- More complex to implement thus slightly slower than reentrant lock

**Implementation factors**

- Release preference - If writer is running, and readers+writers are waiting, preference to writer?
- Reader barging - If reader is running, and readers+writers are waiting, preference to reader? Good for throughput but writer can become starved
- Reentrancy - Are they reentrant
- Downgrading - what if writer lock owners wants only reader lock
- Upgrading - What if reader lock owner also wants writer lock

#### Custom Synchronizer

Conditional queues - Threads waiting for an object lock which reflects certain condition.

Explicit class called Condition for implementing conditional queues (which can be implemented using intrinsic locks too).

Condition is associated with single lock. Lock.newCondition()

**Advantages**

- Fairness in wait
- Timeout facility (flexibility)
