---
title: "Threads"
description: "This post aims to provide a comprehensive understanding of threads and their pratical applications. It covers the fundamentals of threads and offers pratical guidance on how to use them effectively. This post will discuss how to use threads in a program, not at the OS level."
pubDate: "Mar 31 2023"
updatedDate: "Apr 09 2023"
references: "https://www.cs.uic.edu/~jbell/CourseNotes/OperatingSystems/4_Threads.html, https://web.mit.edu/6.005/www/fa14/classes/17-concurrency/, https://os.cs.luc.edu/scheduling.html"
---

<a href="https://github.com/netodotcom/threads" target="_blank" rel="noopener noreferrer">Github repository</a>

Threads are the smallest unit of execution in a program, and they allow multiple tasks to be executed concurrently within the same program. In a multi-threaded application, each thread runs independently and has its own execution path, allowing for parallel processing of tasks.

When working with an API that writes to a database, threads are important because they allow for concurrent database operations. This can significantly improve the performance and responsiveness of the application, as multiple threads can be used to execute database queries or write data to the database simultaneously.

Without threads, database operations would have to be executed sequentially, which could lead to performance issues and slower response times. By using threads, multiple database operations can be executed in parallel, reducing the overall time needed to complete these tasks.

However, it's important to note that concurrent access to a database can also lead to issues like data inconsistency and race conditions. Proper synchronization mechanisms, like locks or semaphores, should be implemented to ensure that the database is accessed safely and consistently by all threads.

# Introduction

Consider the scenario of a computer with a single core where four programs are currently running simultaneaously. To deal with it, the computer must utilize concurrency and *virtual paralelism techniques to handle the four programs running simultaneousy and the associated instructions, despite the computer's capacity being limited to executing only one instruction at a time.
The processor has a unity to thread management (Thread Management Unit - TMU) which make the management access of threads to the CPU and the Scheduling algorithms are responsable to determine which program's instruction gonna be executed next.

* Virtual parallelism is a simulation of multiple processes or threads in a single processor or core.

Consider another scenario of a computer with two cores where four programs are currently running simultaneously. In this case, program 1 and program 2 are using core 1, and program 3 and program 4 are using core 2. 
Let's assume that program 1 has high priority; then, it can be assigned to the entire core 1 while the other programs share core 2.

# Threads synchronization

Techniques like lock, semaphore and synchronization can be utilized to manage resources and resolve concurrency problems effectively.

Click <a href="https://github.com/netodotcom/threads/tree/main/Conflicts" target="_blank" rel="noopener noreferrer">here</a> to see these examples and understand how they can be used.

# Threads states

A thread begins it's life cycle as new and remains in that state until it become runnable.
Once the thread is ready to execute, it does so, and it's subsequent states may be affected by external factors, such as higher-priority threads that need to be executed or any exceptions that the thread may throw.
Assuming no exception occurs, the thread is eventually terminated. It is possible to view many details about threads states using logs (Java has build-in support for thread logging through the ```java.util.logging```) and this topic will be discussed later.

Threads can be in some states:

* #### New
    > When thread has been created but not yet started.


* #### Runnable
    > When thread has been started and ready to be executed but it may not be currently running.


* #### Blocked
    > When thread is temporary unable to run for specific reason.


* #### Waiting
    > When thread is waiting for a condition or event to occur.


* #### Timed waiting
    > When thread is waiting for a specific period of time.

    <a href="https://github.com/netodotcom/threads/blob/main/Sleep/Sleep.java" target="_blank" rel="noopener noreferrer">Here</a> is an example of using the 'sleep' method to put a thread in timed waiting state.


* #### Terminated
    > When thread finish because it was completed or termined due to an exepction or error.

# Priority

When a thread is created, it is possible to define its priority. If no priority is defined then the thread is assigned with normal (default).
In java, there is a priority scale ranging from 1 to 10, and constants MIN_PRIORITY (1), NORMAL_PRIORITY (5) MAX_PRIORITY (10)
The method ```public void setPriority(x)``` can be used to set the thread's priority.

Although the operation system (OS) is responsible for managing and scheduling the execution of threads based on their priorities and OTHERS FACTORS. Therefore, even if a thread has a priority defined, OS has the final say in deciding which thread to execute first.


# Scheduling

OS have a thread scheduling that works with its own algorithms. Each OS, such as Windows, Linux, macOS, android and others has its own unique algorithm. It's an important OS topic and you can find a good reference in this link https://os.cs.luc.edu/scheduling.html
