### steps
- write systemcall
- add it to target files
- compile kernel

#### position of operating system
the lowest level is hardware which consists of physical devices such as ICs, cathode lamps and ..
on top level we've got Michroarchitecture in which physical devices interact with eachother. Normally this levele has CPU registers and a Data Path of ALU.

##### a computer system hierarchy
- applications
- system programs (compilers, editors, shell, command iterpreter)
- operating system
- machine language
- michroarchitecture
- physical devices

##### shell
- is the interface between end user and kernel and its duty is to interprete user commands to into understandable system calls for kernel.
- in old operating systems like MS-DOS shell was about text commands. Howerever, today there are both text and graphical shells
- shell is located at User space, in contrary kernel is located at kernel space

##### systemcall
- as defined it's a method to get services from the kernel
- the picture below simply shows how a system call works:
![](https://github.com/v-nafiseh/Kernel/blob/main/syscall.JPG)

##### steps for adding the systemcall and compiling the kernel
- update os
```sh 
sudo apt update
```
- get the latest version of linux kernel from kernel.org
- check the current kernel version
```sh
uname -r
```
- change directory to new kernel and create a directory for systemcall
```sh
cd linux-version
mkdir mysyscall
cd mysyscall
```
- make a c program for the systemcall
```sh
vim mysyscall.c
```
```c
#include <linux/kernel.h>
#include <linux/syscalls.h>

SYSCALL_DEFINE0(mysyscall)

{
    printk("This is my attempt for a basic syscall.\n");
    return 0;
}
```
- create Makefile and add the proper code
```sh
touch Makefile
echo obj-y : mysyscall.o > Makefile
```
- return back to the kernel dir and add the new syscall to the line containing core-y
```sh
cd ..
vim Makefile
kernel/ certs/ mm/ fs/ ipc/ security/ crypto/ block/ mysyscall
```
- enter the header file add the follwing command
```sh
vim include/linux/syscalls.h
asmlinkage long sys_mysyscall(void);
```
- add your syscall function tp system call table
```sh
vim arch/x86/entry/syscalls/syscall_64.tbl
linenum 64 mysyscall sys_mysyscall
```
- specify number of cores for the process of compile, in this case I allocate 2 cores on my vm
```sh
make -j2
```
- start the process which may take some time according to system resources
```sh
make install -j2
```





