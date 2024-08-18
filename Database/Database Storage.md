# Introduction
Reading /writing to disk is expensive. So it is importance to manage them carefully so that to avoid large stalls and performance degradation.

Even for the databases with terabyte of data, ideally we would like to give the appearance that everything is in memory, even though it actually isn't. 

Random Access ar disk is slower than sequential Access, so the DBMS will want to maximise sequential access.

As a DBMS, we would like to do everything by ourselves, and rely very less on OS.
# Why Not Use OS?

`mmap` helps to take the content that is available on the disk and map it into virtual memory within our process address space. 

Once, it is available in Virtual Memory, our process can jump to any offset in that address space in memory with the OS in the charge to decide which offset is which.

Since the process can now jump to any offset in that address space in memory, the OS is in charge of determing whether or not the object you need is in memory. If not, it the  fetches the page we need and brings it into memory. Here DBMS doesn't handle any of the data management; it simply opens the file and OS moves the data back and forth for all of us. 

Let's take an example from below image.
file:///home/chessman/Downloads/NullvsEmpty(1).png

Let's say user has to access 