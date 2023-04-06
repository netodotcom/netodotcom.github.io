---
title: "Threads"
description: "What are threads and how to deal with it"
pubDate: "Mar 31 2023"
updatedDate: "Apr 05 2023"
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
