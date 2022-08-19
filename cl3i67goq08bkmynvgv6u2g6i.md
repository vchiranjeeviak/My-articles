## Intro to Operating Systems

### What is a computer?

A computer is a device that is used to perform some tasks given to it by a user in a formal format as sequence of instructions.

A computer can be divided into 2 logical parts. They are hardware and software.

- Computer hardware is the set of physical components of the system. It includes devices like monitor, keyboard, mouse etc.
- Computer software is the set of programs (sequence of instructions) stored in and executed by a computer system.

### Software:

There are 2 types of software broadly. They are application software and system software.

- An application software is designed to perform a specific task for the user.
- A system software controls and operates the entire computer system and provides a platform for user to run application software.

### Operating system:

An operating system is a system software which manages all the resources of a computer, both hardware and software, and provides a platform for the user to execute their programs in an efficient and convenient manner.

### Services provided by an operating system:

- Managing the computer hardware.
- Provide the platform to execute application software.
- Act as an interface of the user to interact with the computer hardware.
- Provide ease, convenience and efficiency to the user tasks.

## Terminology:

### Kernel:

A kernel is a part of the operating system which interacts directly with the computer hardware and performs most crucial tasks.

### Micro kernel:

A micro kernel is much smaller in size than a conventional kernel and it supports only the very important (core) functionalities of the operating system.

### Shell:

A shell is a command interpreter which is a part of an operating system that receives commands from the user and gets them executed.

### System call:

Every program run by the user doesn’t contain privileges to interact with the kernel of the OS. This is called user mode. Programs running on user mode can be interrupted by other programs or processes. So, when there are any operations which needs to be done without interruptions, they are run in kernel mode. To run some instructions in kernel mode, the program needs to use system calls. A system call is a mechanism using which a user program can request a service from the kernel for which it doesn’t have the permission to perform.

Process on user mode -> System call -> System call on kernel mode -> next line in user mode

### Booting:

Booting is the process of starting the computer and loading the kernel. Power-on-self-tests (POST) are performed when a computer is turned on. After that a bootstrap loader is executed which resides inside ROM. Bootstrap loader loads the kernel or a more sophisticated loader.