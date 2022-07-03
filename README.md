File objects vs File descriptors in Python
```
File descriptors are a low-level facility for working with files directly provided by the OS kernel. A file descriptor is an integer that identifies the open file in a table of open files kept by the kernel for each process. A number of system calls accept file descriptors, but they are not convenient to work with, typically requiring fixed-width buffers, multiple retries in certain conditions, and manual error handling.

File objects are Python classes that wrap file descriptors to make working with files more convenient and less error-prone. For example, they provide error-handling, buffering, line-by-line reading and are closed when garbage collected.

Built-in open() takes a file name and returns a new Python file object. Note that this is different from os.open()

os.open() takes a file name and returns a new file descriptor. This file descriptor can be passed to other low-level functions, such as os.read() and os.write(), or to os.fdopen().

os.fdopen() takes an existing file descriptor and builds a Python file object around it. It converts a file descriptor to a full file object. It is useful when interfacing with C code or with APIs that only create low-level file descriptors.

So both of these functions provide more close to the system functionality to work with in Python.
```

line in f.readlines() --> loads the entire file
line in f --> reads one line at a time
