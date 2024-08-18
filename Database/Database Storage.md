# Introduction
Reading /writing to disk is expensive. So it is importance to manage them carefully so that to avoid large stalls and performance degradation.

Even for the databases with terabyte of data, ideally we would like to give the appearance that everything is in memory, even though it actually isn't. 

Random Access ar disk is slower than sequential Access, so the DBMS will want to maximise sequential access.

As a DBMS, we would like to do everything by ourselves, and rely very less on OS.
# Why Not Use OS?

`mmap` helps to take the content that is available on the disk and map it into virtual memory within our process address space. 

Once, it is available in Virtual Memory, our process can jump to any offset in that address space in memory with the OS in the charge to decide which offset is which.

Since the process can now jump to any offset in that address space in memory, the OS is in charge of determing whether or not the object you need is in memory. If not, it the  fetches the page we need and brings it into memory. Here DBMS doesn't handle any of the data management; it simply opens the file and OS moves the data back and forth for all of us. 

**Let's take an example from below image.**
![[Pasted image 20240818132846.png]]

Virtual memory is what i see in my process address space, and i can access the mmap files at some starting point. However, these virtual memories must be backed by physical pages, so whenever i touch the page, OS must go ahead and move it into the physical memory space before updating the connection for the virtual memory.

In above image, my process tries to access page one, we will first encounter a page fault because OS will detect that i do not have page one in physical memory. It will then retrieve the page and update the connection of virtual memory to point to it.

This will allow my process to touch it or perform other operations once. Similarly, if i try to access page two and thee and it isn't there. I will encounter a page fault because the OS will block my process and update the wiring. Only then will my thread be able to resume and my process will be able to resume.

**What happens when I want to touch page two? What happens during the process of getting rid of it?**

My process stops working, so I go to the OS, which will block me while it says, "Well, since I don't have any more physical memory, let me go figure out what do these pages—pages one through three—which one should I throw away?" 

The OS will then use its own internal statistics about how these pages are accessed to decide which page to remove, but it won't know anything about what we're doing inside the database system.

But because it only seeds reads and writes, it has no idea what we're doing inside the database system. It doesn't like as a course screen; it doesn't know what queries are; it doesn't know what's in these data pages; it doesn't know what's in these files; therefore, the OS will attempt to decide how to replace things, which is just another issue with eviction. If we rely on the OS to handle this for us, we'll run into a lot more issues.


