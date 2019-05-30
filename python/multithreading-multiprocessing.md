### Multithreading vs Multiprocessing
❓ Multithreading vs Multiprocessing   
[source][1]   

Concurrency and parallelism are related terms but not the same.   

Concurrency is about dealing with a lot of things at same time (gives the illusion of simultaneity) or handling concurrent events essentially hiding latency.   

Parallelism is about doing a lot of things at the same time for increasing the speed.

#### Conclusion
- only one thread running at given time in a Python
- multiprocessing is a parallelism. multithreading is Concurrency
- multiprocessing is for increasing speed. multithreading is for hiding latency
- multiprocessing is best for computations. multithreading is best for IO
- if having CPU heavy tasks, use multiprocessing with `n_process = n_cores` and never more.
- if having IO heavy tasks, use multithreading with `n_threads = m * n_cores` with m a number bigger than 1 which you should tweak on your own. Try many values, measure and choose the one with the best speedup.

### Concurrency with Process, Thread, Coroutine
[source][2]

#### Flash card
front  |  back
--|--
subprocess | provides an API for creating and communicating with secondary processes. It is especially good for running programs that produce or consume text, since the API supports passing data back and forth through the standard input and output channels of the new process.
signal |  exposes the Unix signal mechanism for sending events to other processes. The signals are processed asynchronously, usually by interrupting what the program is doing at the time the signal arrives. Signalling is useful as a coarse messaging system, but other inter-process communication techniques are more reliable and can deliver more complicated messages.
threading | includes a high-level, object oriented, API for working with concurrency from Python. Thread objects run concurrently within the same process and share memory. Using threads is an easy way to scale for tasks that are more I/O bound than CPU bound.
multiprocessing |  mirrors threading, except that instead of a Thread class it provides a Process. Each Process is a true system process without shared memory, but multiprocessing provides features for sharing data and passing messages between them so that in many cases converting from threads to processes is as simple as changing a few import statements.
asyncio | provides a framework for concurrency and asynchronous I/O management using either a class-based protocol system or coroutines. asyncio replaces the old asyncore and asynchat modules, which are still available but deprecated.
concurrent.futures | provides implementation of thread and process-based executors for managing resources pools for running concurrent tasks.


#### Flash card
front  |  back
--|--
  many threads running at given time in a python |   false
multiprocessing or multithreading is concurrency |   multithreading
multiprocessing or multithreading is parallelism |   multiprocessing
multiprocessing or multithreading is best for computations |   multiprocessing
multiprocessing or multithreading is best for IO | multithreading
if having CPU heavy tasks, use multiprocessing with n_process = ___ and never more. | n_cores


❓ Process, Thread, Coroutine   

[3][3]

-----
[1]: https://medium.com/contentsquare-engineering-blog/multithreading-vs-multiprocessing-in-python-ece023ad55a
[2]: https://pymotw.com/3/concurrency.html
[3]: https://medium.com/@bfortuner/python-multithreading-vs-multiprocessing-73072ce5600b