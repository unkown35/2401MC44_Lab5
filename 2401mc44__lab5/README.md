# Operating Systems Lab – Assignment 5

**Name:** Sai Vignan  
**Roll No.:** 2401MC44

This package contains the xv6 implementation for Assignment 5, Questions 1–3.

## Q1 – Peterson's Algorithm

Two processes share `flag\[2]`, `turn`, and `shared\_counter` through the shared-memory page. The shared state is initialized before `fork()`. Peterson's `flag` and `turn` variables provide the actual mutual exclusion.

Expected final counter: 20.

## Q2 – Producer–Consumer

A circular buffer of default size 5 is shared by a producer and consumer. The producer creates integers 1–20. Synchronization uses two counting semaphores (`EMPTY`, `FULL`) and one binary semaphore (`MUTEX`). The semaphore implementation uses xv6 sleep/wakeup.

## Q3 – Readers–Writers

The program creates 3 readers and 2 writers. `read\_count` is protected by `RC\_MUTEX`; `RESOURCE` provides exclusive writer access and reader-group access. `TURNSTILE` prevents indefinite writer starvation while allowing concurrent readers.

Expected final `shared\_data`: 10.

Five philosopher processes use five binary fork semaphores. Resource ordering is used: every philosopher acquires the lower-numbered fork first and then the higher-numbered fork. This removes circular wait and prevents deadlock. Each philosopher performs 5 cycles.

## Shared memory

`shm\_get()` allocates one persistent physical page and maps it at `SHM\_VA` into each process that requests it. `SHM\_VA` is outside the normal process size, so it is not copied by ordinary `fork()` user-memory copying; children map the same physical page through `shm\_get()`.

## Files

* `kernel/` – kernel changes
* `user/` – the four assignment programs
* `Makefile` – kernel objects and user programs
* `output\_logs/` – supplied screenshots preserved unchanged

## Running

From the xv6 directory:

```text
make clean
make qemu
```

Inside xv6:

```text
peterson
prodcons
readwrite
dining
```

The screenshots in `output\_logs/` are the supplied screenshots 

