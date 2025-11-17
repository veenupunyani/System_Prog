# System_Prog

## Pipe Synchronization Demo

This repository contains a C program demonstrating process synchronization using pipes.

### pipe_demo.c

A program illustrating inter-process communication and synchronization using pipes. 

**Author:** Sourav Mukherjee (sourav@fdu.edu)

**Concept:**
- A parent process creates two child processes (C1 and C2)
- Each child completes two tasks (T1 and T2)
- The pipe is used for synchronization: when both children close their write end after completing T1, the parent receives EOF
- Parent detects this synchronization point and confirms all children completed their first task
- Parent then waits for both children to complete T2 and exit

### How to Compile

```bash
gcc -Wall -o pipe_demo pipe_demo.c
```

### How to Run

```bash
./pipe_demo
```

### Expected Output

```
Child 0 completed task: T1
Child 1 completed task: T1
All children have completed their first task.
Child 0 completed task: T2
Child 1 completed task: T2
All children have completed their second task as well.
```

### Key Concepts Demonstrated

1. **Pipe creation** - Using `pipe()` system call
2. **Process creation** - Using `fork()` to create child processes
3. **Process synchronization** - Using pipe EOF to synchronize parent with children
4. **Proper resource management** - Closing unused pipe ends in each process
5. **Process waiting** - Using `wait()` to wait for child processes to complete