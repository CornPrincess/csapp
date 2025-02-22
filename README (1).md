# Chapter 1 A Tour of Computer Systems

## 1.1 Information Is Bits + Context

```c
/* $begin hello */
#include <stdio.h>

int main() 
{
    printf("hello, world\n");
    return 0;
}
/* $end hello */
```

 Files such as hello.c that consist exclusively of ASCII characters are known as **text files**.All other files are known as **binary files**.

**All information in a system is represented as a bunch of bits.The only thing that distinguishes different data objects is the context in which we view them. For example, in different contexts, in different contexts, the same sequence of bytes might represent an integer, floating-point number, character string, or machine instruction.**

## **1.2 Programs Are Translated by Other Programs into Different Forms**

preprocessor

compiler

assembler&#x20;

linker

the four phase are known collectively as the compilation system,

## 1.4 Processor Read and Interpret Instructions Stored in Memory

### 1.4.1 Hardware Organization of a System

**Bus**\
****Buses are typically designed to transfer** fixed size chunks of bytes knowns as words**,The number of bytes in a word (the word size) is a **fundamental system parameter that varies across systems.**

**Processor**\
We say that a a processor appears to be a simple implementation of its instruction set architecture.

## 1.5 Cache Matter

The processor-memory gap continues to increase. It is easier and cheaper to make processors run faster than it is to make main memory run faster.

To deal with processor-memory gap, system designers include smaller, faster storage devices called **cache memories **that serve as temporary staging areas for information that the processor is likely to need in the near feature.

## 1.6 Storage Devices Form a Hierarchy

The main idea of a memory hierarchy is that storage at one level serves as a cache for storage at the next lower level.

## 1.7 The Operating System Manages the Hardware

The operating system has two main purposes:\
1.to protect the hardware from misuse by runaway application\
2.to provide the application with simple and uniform mechanism for complicated and often wildly different low-level hardware devices.

**Processes**\
****When a program such as hello runs on a modern system, the operating system provides the illusion that the program is the only one running on the system. The program appears to have exclusive use of both the processor, main memory, and I/O devices. The processor appears to execute the instructions in the program, one after the other, without interruption. And the code and data of the program appear to be the only objects in the system's memory. These illusions are provided by the notion of a process, one of the most important and successful ideas in computer science.\
向 hello 这样的程序在现代系统上运行时，操作系统会提供一种假象，就好像系统上只有这个程序在运行。程序看上去是独占地使用处理器、内存和IO设备。处理器看上去就像在不间断地一条接一条地执行程序中的指令，即改程序的代码和数据是系统内存中唯一的对象。这些假象是通过进程的概念来实现的，进程是计算机科学中最重要和最成功的概念之一。

**A process is the operating system's abstraction for a running program. Multiple processes can run concurrently(并发) on the same system, and the each process appears to have exclusive use of he hardware. Traditional systems could only execute only one program at one time, while newer multicore processors can execute multiple programs simultaneously. **\
****The operating system performs this interleaving with a mechanism known as **context switching.**\
****The transition from one process to another is managed by the operating  system **kernel. **The kernel is the portion of the operation system code that is always resident in memory.

**Thread**\
In modern systems, a process can actually consist of multiple execution units, called threads, each running in the context of the process and sharing hte same code and global data.

** Virtual Memory**\
Virtual Memory is an abstraction that provides each process with the illusion that it has exclusive use of the main memory. Each process has the same uniform view of memory , which is known as its **virtual address space.**

**File**\
** **A file is a sequence of bytes, nothing more and nothing less.

## 1.8 System Communicate with Other Systems Using Networks

## 1.9 Important Themes

### 1.9.1 Amdahl's Law

To significantly speed up the entire system, we must improve the speed of a very large fraction of the overall system.\
**Amdahl's law describes a general principle for improving any process. In addition to its application to speeding up computer systems, it can guide a company trying to reduce the cost of manufacturing razor blades, or a student trying to improve his or her grade point average. Perhaps it is most meaningful in the world of computers, where we routinely improve performance by factors of 2 or more. Such high factors ca only be achieved by optimizing large parts of a system.**\
****

### **1.9.2 Concurrency and Parallelism**

We use term **concurrency** to refer to the general concept of a system with multiple, simultaneous activities, and the term **parallelism** to refer to the use of concurrency to make a system run faster.

**Thread-Level Concurrency**\
With threads, we can even have multiple control flows executing within a single process. Traditionally, this concurrent execution was only **simulated**, by having a simple computer rapidly switch among its executing processes.\
Most computing was done by a single processor, even if that processor had to switch among multiple tasks, this configuration is known as a **uniprocessor** system.\
The use of multiprocessing can improve system performance in two ways. First, it reduces the need to simulate concurrency when performing multiple tasks. Second, it can run a single application program faster, but only if that program is expressed in terms of multiple threads that can effectively execute in parallel.

**Instruction-Level Parallelism**\
At a much lower level of abstraction, modern processors can **execute multiple instructions at one time**, a property known as instruction-level parallelism. Processors that can sustain execution rates faster than 1 instruction per cycle are known as **superscalar processor.**

**Single-Instruction, Multiple-Data(SIMD) Parallelism**\
****At the lowest level, many modern processors have special hardware that allows a single instruction to cause multiple operations to be performed in parallel, a mode known as single-instruction, multiple-data(SIMD) parallelism.

### 1.9.3 The Importance of Abstractions in Computer Systems

A major theme in computer systems is to provide abstract representations at different levels to hide the complexity of the actual implementations.

## 1.10 Summary

The operation systems kernel serves as an intermediary between the application and the hardware. It provides three fundamental abstractions:\
1\. Files are abstractions for I/O devices.\
2\. Virtual memory is an abstraction for both main memory and disks.\
3.Processes are abstractions for the processor, main memory and I/O devices.
