## Collections

### Resources

- [OCA/OCP Java SE 7 Programmer](https://www.amazon.com/Programmer-Study-1Z0-803-1Z0-804-Certification/dp/0071772006/ref=asap_bc?ie=UTF8) (book) 
- [Cheat sheet](http://files.zeroturnaround.com/pdf/zt_java_collections_cheat_sheet.pdf) (PDF)
- [Effective Java study notes](topics/design/effective-java.md)
- [Time complexity] (https://codenza.app/java-collections/) 

### Table of contents

- [Lists](#lists)
  * [ArrayList](#arraylist)
  * [LinkedList](#linkedlist)
  * [Stack](#stack)
  * [Vector](#vector)
  * [CopyOnWriteArrayList](#copyonwritearraylist)
  * [Collections.synchronizedList](#collectionssynchronizedlist)
- [Sets](#sets)
  * [HashSet](#hashset)
  * [LinkedHashSet](#linkedhashset)
  * [TreeSet](#treeset)
  * [ConcurrentSkipListSet](#concurrentskiplistset)
  * [CopyOnWriteArraySet](#copyonwritearrayset)
  * [EnumSet](#enumset)
- [Maps](#maps)
  * [HashMap](#hashmap)
  * [HashMap implementation details](#hashmap-implementation-details)
  * [LinkedHashMap](#linkedhashmap)
  * [Hashtable](#hashtable)
  * [ConcurrentHashMap](#concurrenthashmap)
  * [TreeMap](#treemap)
  * [ConcurrentSkipListMap](#concurrentskiplistmap)
- [Queues](#queues)
  * [LinkedList](#linkedlist-1)
  * [ArrayBlockingQueue](#arrayblockingqueue)
  * [LinkedBlockingQueue](#linkedblockingqueue)
  * [ConcurrentLinkedQueue](#concurrentlinkedqueue)
  * [Deque classes](#deque-classes)
  * [PriorityQueue](#priorityqueue)
  * [PriorityBlockingQueue](#priorityblockingqueue)
  * [DelayQueue](#delayqueue)
  * [SynchronousQueue](#synchronousqueue)
- [equals and hashCode](#equals-and-hashcode)
- [Collections class](#collections-class)
  * [Utility methods](#utility-methods)
  * [Methods returning wrapped instances](#methods-returning-wrapped-instances)
- [Hierarchy and classes](#hierarchy-and-classes)

---

### Lists

#### ArrayList
- class ArrayList<E> extends AbstractList<E> implements List<E>, RandomAccess, Cloneable, Serializable
- Backed by array (which are co-located in memory), thus fast iteration and get(i) operation.
- Slow inserts when the backed array is full and has to double in size.
- Fail-fast iterators, which can throw ConcurrentModificationException.
- Add is O(n) - When element is added to middle of list, all elements on the right have to be moved.  
- [Use Case](http://stackoverflow.com/a/322742/3494368) - When iterations outnumber number of read/writes. 
    
#### LinkedList

- class LinkedList<E> extends AbstractSequentialList<E> implements List<E>, Deque<E>, Cloneable, Serializable
- Chain of nodes referencing each other (doubly linked list).
- No co-location of nodes, pointers need to be chased for next element, thus slow iterations and get(i) operation.
- Fail-fast iterators, which can throw ConcurrentModificationException. 
- Implements Queue interface, thus allows offer/pop/peek operations.
- Add is O(1) - Adding element in middle of list is just adjusting the node pointers. 
- Internally uses references (~ to skiplist) to optimize iterations. 
- [Use Case](http://stackoverflow.com/a/322742/3494368) - Lot of inserts in middle of the list.
   
| Operation       | ArrayList                         | LinkedList                |
|-----------------|-----------------------------------|---------------------------|
| get(i)          | O(1)                              | O(n)                      |
| add()           | O(1) amortized                    | O(1)                      |
| remove(i)       | O(n) Remove and move all elements | O(n)  Iterate then remove |
| iterator.remove | O(n)                              | O(1)                      |
   
#### Stack

- For stack operations push/pop/peek.
- Not used anymore. Recommended to use Deque implementations.

#### Vector

- Synchronized version of list.
- Not used anymore. Recommended below mentioned alternatives. 
    
#### CopyOnWriteArrayList

- class CopyOnWriteArrayList<E> implements List<E>, RandomAccess, Cloneable, Serializable
- Thread-safe. 
- For every write operation (add, set, remove, etc), it makes a new copy of the elements in the list. and for the read operations (get, iterator, listIterator, etc), it works on a different copy. 
- It locks the list during write operation only, so no lock during read operation therefore, multiple threads executing read operations  concurrently.
- It is a fail-safe iterator.Avoids ConcurrentModificationException since iteration can continue in original copy, and insert results in new copy. 
- High memory usage (more pressure on GC) due to the resulting copies.
- It can safely iterate outside the synchronized block.
- Use case - It is best to use when ArrayList is small or read operation are greater then write operation.
    
#### Collections.synchronizedList
- class SynchronizedList<E> extends Collections.SynchronizedCollection<E> implements List<E>
- Thread-safe. It locks the whole list for thread-safety during both read or write operation.
- Can be slow due to mutual exclusion.
- Iteration of list should be inside synchronized block otherwise it will face non-deterministic behaviour.
- Can throw ConcurrentModificationException if (above mentioned) synchronization not done during iteration.
- Use Case - It is best to use when arraylist is large and write operation are greater than read operation in list.
---

### Sets

Collection of unique elements. No duplicates. 

#### HashSet

- class HashSet<E> extends AbstractSet<E> implements Set<E>, Cloneable, java.io.Serializable
- Backed by HashMap. 
- It is unsorted, unordered and non-indexed based collection class.
- HashSet can have only one Null element
- Performance can vary based on hashCode implementation.
- Constant time get/remove/add/contains (subject to above point).
- Fail-fast iterators.
- Choosing an initial capacity that's too high can waste both space and time. On the other hand, choosing an initial capacity that's too low wastes time by copying the data structure each time it's forced to increase its capacity. If you don't specify an initial capacity, the default is 16.
- The HashSet class has one other tuning parameter called the load factor. HashSet size grows as per load factor defined or default double size.
- (https://www.w3resource.com/java-tutorial/java-hashset.php)
    
#### LinkedHashSet
- class LinkedHashSet<E> extends HashSet<E> implements Set<E>, Cloneable, java.io.Serializable 
- Insertion order is retained. 
- Uses doubly-linked list to maintain the order.
- Iteration can be slower due to this.
- Other features, same as HashSet above (except iteration)

#### TreeSet
- class TreeSet<E> extends AbstractSet<E> implements NavigableSet<E>, Cloneable, java.io.Serializable
- Elements sorted by their natural order (or Comparator passed in constructor).
- Log(n) time for add/remove/contains operations.
- Navigable (floor, ceiling, higher, lower, headSet, tailSet operations).
- Fail fast iterators.
- TreeSet is implemented using a Self Balancing Binary Search Tree (Red-Black Tree). TreeSet is backed by TreeMap in Java.
- TreeSet doesn’t allow null Object and throw NullPointerException, Why, because TreeSet uses compareTo() method to compare keys and compareTo() will throw java.lang.NullPointerException. Till 1.6 null was accepted only as the first element.
- TreeSet uses compare() and compareTo() methods to compare the objects
- While working with large amount of data access and retrieval is faster with TreeSet
- If we are short on memory, we should go for the TreeSet
- HashSet‘s performance can be tuned using the initialCapacity and loadFactor, which is not possible for the TreeSet.
 

#### ConcurrentSkipListSet
- class ConcurrentSkipListSet<E> extends AbstractSet<E> implements NavigableSet<E>, Cloneable, java.io.Serializable
- Thread-safe.
- Doesn’t allows null values.
- Sorted set just like TreeSet but it is also scalable and concurrent so ConcurrentSkipListSet is thread-safe and can be accessed by multiple threads safely.
- Operations like add and remove are done atomically using compare and swap (CAS). These are lock-free so overhead of synchronization is not there
- Log(n) time for add/remove/contains operations.
- Navigable (floor, ceiling, higher, lower, headSet, tailSet operations).
- Size method is not constant time operation. 
- Weakly consistent iterators (do not throw ConcurrentModificationException but also __may not__ reflect concurrently added items).
- Thus, bulk operations (addAll, removeAll, retainAll, containsAll etc) are not guaranteed to be atomic.

#### CopyOnWriteArraySet
- class CopyOnWriteArraySet<E> extends AbstractSet<E> implements Serializable
- Backed by CopyOnWriteArrayList
- Thread-safe. 
- Slow. Operations have to iterate through the array for most operations.  
- Suited to cases where the set is relatively small and reads far outweight writes. Any modification of the set is expensive (since a brand new copy is created each time), but reads are non-blocking.
- Traversal via iterators is fast and cannot encounter interference from other threads.
 
#### Collections.synchronizedList
- class SynchronizedList<E> extends Collections.SynchronizedCollection<E> implements List<E>
- Thread-safe. It locks the whole set for thread-safety during both read or write operation.
- Can be slow due to mutual exclusion.
- Iteration of set should be inside synchronized block otherwise it will face non-deterministic behaviour.
- Can throw ConcurrentModificationException if (above mentioned) synchronization not done during iteration.
- Use this if you only have low concurrency, and want to be sure all changes are immediately visible to the other threads.

#### Collections.newSetFromMap(new ConcurrentHashMap())
- Returns a set backed by the specified map.
- Basic options are (on average, if you have a good and fast hashCode()) in O(1) (but might degenerate to O(n)), like for HashMap/HashSet.
- Limited concurrency for writing (the table is partitioned, and write access will be synchronized on the needed partition), while read access is fully concurrent to itself and the writing threads (but might not yet see the results of the changes currently being written). - The iterator may or may not see changes since it was created, and bulk operations are not atomic.
- Resizing is slow (as for HashMap/HashSet), thus try to avoid this by estimating the needed size on creation (and using about 1/3 more of that, as it resizes when 3/4 full).
- Use this when you have large sets, a good (and fast) hash function and can estimate the set size and needed concurrency before creating the map.
 
#### EnumSet

- To be used with Enum types.
- Very efficient and fast (backed by bit-vectors).
- Weakly consistent iterators. 
- Nulls not allowed.

---

### Maps

#### HashMap

- key, value pairs.
- Permits a null key, and null values.
- Iteration order not guaranteed.
- Throws ConcurrentModificationException.
- [Article detailing implementation](http://www.deepakvadgama.com/blog/java-hashmap-internals/).

#### HashMap implementation details

- Backed by array (buckets), array-size is known as table-size.
- Position in array = element-hash % table-size. 
- If elements end up in same bucket, they are added to linked-list (or a balanced red-black tree).
- O(1) access (if hashcode properly distributes the values, else O(n) for linked-list & O(log(n)) for tree.
- Load factor - 0.75 default, decides when table-size should increase (double). 
- Bigger load-factor - more space-efficient, reduced speed (due to more elements in same bucket).
- Lower load-factor - less space-efficient, more speed (less, ideally 1 element in 1 bucket).
- Initial table-size = 16.

#### LinkedHashMap

- Insertion order is retained.

#### Hashtable

- Thread-safe.
- Not used anymore, ConcurrentHashMap recommended.

#### ConcurrentHashMap

- Thread-safe.
- Fine grained locking called striped locking (map is divided into segments, each with associated lock. Threads holding different locks don't conflict).
- Improved performance over Hashtable.

#### TreeMap

- Sorted by keys. 
- Uses Red-Black tree implementation. 

#### ConcurrentSkipListMap

- Thread-safe version of TreeMap.
- Navigable (floor, ceiling, higher, lower, headSet, tailSet operations).

#### IdentityHashMap

- Uses == operator when comparing keys and values, instead of equals method. 
- Uses System.identityHashCode(object) instead of hashCode(). 
- Initial capaity of IndentityHashMap is 21.
- If you see the below output for both IdentityHashMap and HashMap, you can find that IdenityHashMap allows duplicate keys and values(bcz of reference comparision), where as HashMap doesn’t allow(bcz of Object comparision).
- It's not a general purpose Map because it doesn't use equals() method for comparing keys, hence also breaks Map interface's contract.

#### WeakHashMap
- WeakReference: When an object is assigned with some value, and it’s not reachable then that value will be removed/garbage collected.
- StrongReference: By default any object in java are StrongReference, i.e. they garbage collected only if there are no reference to it.
  User user = new User();
- WeakHashMap works on weak references, i.e. when a key of WeakHashMap is not in use( or assigned to null) and garbage collected, then that entry will be removed from it.
- Quite useful for Caching. 
---

### Queues

#### LinkedList

- Implements Queue interface. 
- offer, peek, poll operations.
- Use case - task queues

#### ArrayBlockingQueue

- Thread-safe.
- Backed by array. Thus bounded in size.  
- Adding element to full queue results in blocking.
- Polling an empty queue results in blocking.
- Uses single-lock double condition algorithm
- Use case - Producer consumer problem.
    
#### LinkedBlockingQueue

- Thread-safe.
- Backed by linked-list.
- Optionally bounded in size. Takes maxSize as constructor argument.
- Variant of the "two lock queue" algorithm and it has 2 locks 2 conditions ( takeLock , putLock).


#### ConcurrentLinkedQueue

- Unbounded queue which is thread-safe. 
- Non-blocking there are no put() or take() methods which will block if required
- Uses CAS (Compare-And-Swap) for more throughput. Also known as lock free. 

#### Deque classes

- ArrayDeque - Double ended queue. Backed by array. Can throw ConcurrentModificationException.
- LinkedList - Implements Deque interface.  
- LinkedBlockingDeque
- ConcurrentLinkedDeque

#### PriorityQueue

- Elements sorted based on their natural order (or Comparator provided in Constructor).
- Use case - task queues where tasks can have different priorities.
    
#### PriorityBlockingQueue

- Thread-safe.
- Unbounded queue and grows dynamically.
- The default initial capacity is 11.
- Objects added to PriorityBlockingQueue MUST be comparable otherwise it throws ClassCastException.
- It does not allow NULL objects.
    
#### DelayQueue

- An unbounded blocking queue of Delayed elements
- DelayQueue is a specialized Priority Queue that orders elements based on their delay time.
- If no delay has expired, then there is no head and poll will return null.
- Elements added, are available to be removed only after their delay-time is expired.
- Queue does not permit null elements

#### SynchronousQueue

- SynchronousQueue is more of a handoff. 
- Holds single element internally.
- Blocks for both producer and consumer to arrive.
- An element cannot be inserted if the consumer take() call is going to take some time to consume it..
- Use case - For safe/atomic transfer of objects between threads (cachedThreadPool)

#### TransferQueue

- Concurrent blocking queue implementation in which producers may wait for receipt of messages by consumers..
- LinkedTransferQueue class is an implementation of TransferQueue in Java.
- Unbounded queue on linked nodes.
- Queue orders elements FIFO (first-in-first-out) with respect to any given producer.
- LinkedTransferQueue is thread safe.
- It does not allow NULL objects.
- blocking insertion and retrieval operations.
- TransferQueue may be useful for example in message passing applications in which producers sometimes (using method transfer()) await receipt of elements by consumers invoking take or poll, while at other times enqueue elements (via method put()) without waiting for receipt.


---

### equals and hashCode

- equals required for all collections. 
- equals and hashCode required for Maps and Sets (which are backed by Maps).

---

### Collections class

#### Utility methods

- sort(list, key) - guarantees stable sort
- reverse 
- reverseOrder - returns Comparator for reversed order
- shuffle
- rotate(list, distance) - rotates elements by the distance specified 
- binarySearch(list, key) 
    + list should be sorted else can get unpredictable results 
    + log(n) if list implements RandomAccess, else O(n)
    + RandomAccess - Marker interface that says, collection supports fast random access, get(i). Typically backed by arrays. 

#### Methods returning wrapped instances

- empty - emptyList, emptySet, emptyMap etc.
- synchronized - synchronizedList, synchronizedSet, synchronizedMap etc. 
- unmodifiable - unmodifiableList, unmodifiableSet, unmodifiableMap etc. 
- singleton(t) - singleton (returns set), singletonList, singletonMap etc.

---

### Hierarchy and classes

<image src="../../images/collection-hierarchy-2.png">

<image src="../../images/map-hierarchy-2.png">
