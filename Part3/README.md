# Reasons for concurrency and parallelism


To complete this exercise you will have to use git. Create one or several commits that adds answers to the following questions and push it to your groups repository to complete the task.

When answering the questions, remember to use all the resources at your disposal. Asking the internet isn't a form of "cheating", it's a way of learning.

 ### What is concurrency? What is parallelism? What's the difference?
 > Concurrency is when two separate processes sharing one cpu core have their operations interwoven in such a a way that they functionally run at the same time. Parallelism is when two processes are actually running at the same time (for example in two separate cores on a cpu).
 
 ### Why have machines become increasingly multicore in the past decade?
 > Having multiple cores allows for more computation without increasing the cpu clock frequency. As a rule of thumb, increasing the clock frequency by a factor `a` increases the power consumption of a cpu by `a^3`, as one needs to increase the voltage to increase the frequency. This leads to having more cores instead of higher frequencies being much more power efficient, which is critical in mobile and IoT systems which run on batteries. The rise of the smartphone probably led to a bigger push for multicore machines in the last decade.
 
 ### What kinds of problems motivates the need for concurrent execution?
 (Or phrased differently: What problems do concurrency help in solving?)
 > Concurrent execution is useful because you often want your system to do several things seemingly at once, while being sure that one thing going wrong wont destroy other functionality. If the processes are running serially, one process hanging or crashing will stop all other processes from running. Essentially, processes which are conceptually independent should also be independent in code.
 
 ### Does creating concurrent programs make the programmer's life easier? Harder? Maybe both?
 (Come back to this after you have worked on part 4 of this exercise)
 > As with all new tools one learns in programming, it can be a bit time consuming and frustrating in the beginning. However, after having gone through that, one now has a very effective and useful tool. In this exercise, we have not yet learned to use mutexes or other locks to make sure two threads aren't reading from/writing to a resource in the wrong order, so the result is disappointing. In the future, however, we will have the knowlegde to avoid these problems, making our life easier by creating concurrent programs.
 
 ### What are the differences between processes, threads, green threads, and coroutines?
 > Paraphrased from Robert S. Barnes on StackOverflow, who in return got it from Tanenbaum's *Modern Operating Systems 3e*:
 > A process has its own address space with code and data, and its own resources to work with. A process can have one or more threads, which can share these resources along with the address space.
 > Paraphrased from Wikipedia's article *Green threads*:
 > Green threads are threads that execute in a virtual machine or runtime library, instead of run and managed natively by a kernel.
 > Paraphrased from Wikipedia's article *Coroutine*:
 > A coroutine is a part of a program which can yield to another part of the program (stops running and lets that part run), while still retaining its state so execution can resume when some part of the program yields back.

 ### Which one of these do `pthread_create()` (C/POSIX), `threading.Thread()` (Python), `go` (Go) create?
 > They create threads
 
 ### How does pythons Global Interpreter Lock (GIL) influence the way a python Thread behaves?
 > Because of the GIL, python cannot run threads in parallel (only concurrently), and therefore cannot utilize a multicore CPU.
 
 ### With this in mind: What is the workaround for the GIL (Hint: it's another module)?
 > There is a module for python named `multiprocessing` which seems to be made for sidestepping this issue.
 
 ### What does `func GOMAXPROCS(n int) int` change? 
 > The number of CPU cores which can be engaged in executing the user's go code at a time. So calling this with `n=1` will remove parallelism (concurrency will still be possible however).
