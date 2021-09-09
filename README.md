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








