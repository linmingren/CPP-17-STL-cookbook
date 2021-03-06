# 第9章 并行和并发

C++11之前，C++原生不支持并行。但这并不意味着对于线程的操作无法进行，只不过需要使用对应的系统库的API进行操作，因为线程与操作系统是不可分开来讨论的。

随着C++11标准的完成，我们有了std::thread，其能给予我们可以在所有操作系统上可移植的线程操作。为了同步线程，C++11也添加了互斥量，并且对一些RAII类型的锁进行了封装。另外，std::condition_variable也能够灵活的在线程间，进行唤醒操作。

另一些有趣的东西就是std::async和std::future——我们可以将普通的函数封装到std::async中，可以在后台异步的运行这些函数。包装后函数的返回值则用std::future来表示，函数的结果将会在运行完成后，放入这个对象中，所以我们可以在函数完成前，做点别的事情。

另一个STL中值得一提提升就是*执行策略*，其被添加到已有的69中算法中。这样就意味着，我们可以对现有的STL算法不做任何修改，就可以享受其并行化带来的性能提速。

本章中，我们将通过例子来了解其中最为核心的部分。之后，我们也将了解到C++17对并行的支持。我们不会覆盖所有的细节，但是比较重要的部分，我们肯定会介绍。本书会帮助你对并行编程机制快速的进行了解，至于详细的介绍，我们可以在线对C++17 STL文档进行查阅。

最后，本章中最后两节值的注意。倒数第二节中，我们将并行化[第6章的ASCII曼德尔布罗特渲染器](content/chapter6/chapter6-5-chinese.md)，使用STL进阶式用法，就是为了让代码改动程度最小。最后一节中，我们将实现一个简单的库，其可以用来帮助我们隐式，并且自动化的并行执行复杂的任务。



