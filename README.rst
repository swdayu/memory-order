有关并发程序内存顺序同步问题的整理
==================================

内存顺序（Memory Order）同步问题是多线程编程中一个至关重要的概念，它主要用于规定在多
线程环境下，不同线程对共享内存的访问和修改操作在何时以及如何对其他线程可见。在现代计算
机系统里，为了提升性能，编译器、CPU 可能会对指令进行重排，同时 CPU 缓存也会对数据的可
见性产生影响。同步内存顺序的存在就是为了对这些行为加以约束，保证多线程程序的正确性。

常见的内存顺序同步模型包括：顺序一致性模型（Sequentially Consistent Ordering）、获
取释放语义模型（Acquire - Release Semantics）、宽松顺序模型（Relaxed Ordering）。

C/C++ 标准库提供的内存顺序相关设施： ::

    enum memory_order {
        memory_order_relaxed,
        memory_order_consume,
        memory_order_acquire,
        memory_order_release,
        memory_order_acq_rel,
        memory_order_seq_cst
    };
    void atomic_thread_fence(memory_order sync) noexcept;
    void atomic_signal_fence (memory_order sync) noexcept;
    T kill_dependency(T y) noexcept;

参考链接（References）

* https://en.cppreference.com/w/c/language/atomic
* https://en.cppreference.com/w/c/atomic/memory_order
* https://cplusplus.com/reference/atomic/memory_order
* https://learn.microsoft.com/en-us/cpp/standard-library/atomic
* https://gcc.gnu.org/wiki/Atomic
* https://gcc.gnu.org/onlinedocs/gcc/_005f_005fatomic-Builtins.html
* https://research.swtch.com/mm (memory models)

