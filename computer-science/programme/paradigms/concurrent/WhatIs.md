# What Is Concurrent Programming ？
## 并发级别
* 阻塞
```md
是指一个线程进入临界区后，其它线程就必须在临界区外等待，待进去的线程执行完任务离开临界区后，其它线程才能再进去。
```
* 无饥饿
```md
线程排队先来后到，不管优先级大小，先来先执行，就不会产生饥饿等待资源，也即公平锁；
相反非公平锁则是根据优先级来执行，有可能排在前面的低优先级线程被后面的高优先级线程插队，就形成饥饿。
```
* 无障碍
```md
共享资源不加锁，每个线程都可以自由读写，但监测到被其他线程修改过则回滚操作，重试直到单独操作成功；
风险就是如果多个线程发现彼此修改了，所有线程都需要回滚，就会导致死循环的回滚中，造成死锁。
```
* 无锁
```md
无锁是无障碍的加强版，无锁级别保证至少有一个线程在有限操作步骤内成功退出，
不管是否修改成功，这样保证了多个线程回滚不至于导致死循环。
```
* 无等待
```md
无等待是无锁的升级版，并发编程的最高境界，无锁只保证有线程能成功退出，
但存在低级别的线程一直处于饥饿状态，无等待则要求所有线程必须在有限步骤内完成退出，
让低级别的线程有机会执行，从而保证所有线程都能运行，提高并发度。
```
## 并发效率
* Amdahl
```md
S=1/(1-a+a/n)
其中，a为并行计算部分所占比例，n为并行处理结点个数。
这样，当1-a=0时，(即没有串行，只有并行)最大加速比s=n；
当a=0时（即只有串行，没有并行），最小加速比s=1；
当n→∞时，极限加速比s→ 1/（1-a），这也就是加速比的上限。
```
* Gustafson
```md
系统优化某部件所获得的系统性能的改善程度，取决于该部件被使用的频率，或所占总执行时间的比例。
```