- https://www.sourceware.org/gdb/documentation/

# gnu-m4
- https://www.gnu.org/software/m4/
- 옛날코드 찾음
  - https://github.com/tar-mirror/gnu-m4
- https://ftp.gnu.org/gnu/m4/

# Toturial(GBD)
- [(240804)Reverse Engineering 101 tutorial with the amazing Stephen Sims! | David Bombal](https://youtu.be/5FXrCHLAJZM?si=DAJsFN_ceEJef6El)

# gdb

- `main.c`

```c
#include <stdio.h>

int main()
{
    printf("Hello World");

    return 0;
}
```

```gdb
(gdb) info functions
All defined functions:

File main.c:
11:     int main();

Non-debugging symbols:
0x0000000000001000  _init
0x0000000000001040  __cxa_finalize@plt
0x0000000000001050  printf@plt
0x0000000000001060  _start
0x0000000000001090  deregister_tm_clones
0x00000000000010c0  register_tm_clones
0x0000000000001100  __do_global_dtors_aux
0x0000000000001140  frame_dummy
0x000000000000116c  _fini

(gdb) b main
Breakpoint 1 at 0x1151: file main.c, line 13.
(gdb) b 15
Breakpoint 2 at 0x1165: file main.c, line 15.
(gdb) run
Starting program: /home/a.out 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".

Breakpoint 1, main () at main.c:13
13          printf("Hello World");

(gdb) disassemble main
Dump of assembler code for function main:
   0x0000000000001149 <+0>:     endbr64
   0x000000000000114d <+4>:     push   %rbp
   0x000000000000114e <+5>:     mov    %rsp,%rbp
   0x0000000000001151 <+8>:     lea    0xeac(%rip),%rax        # 0x2004
   0x0000000000001158 <+15>:    mov    %rax,%rdi
   0x000000000000115b <+18>:    mov    $0x0,%eax
   0x0000000000001160 <+23>:    call   0x1050 <printf@plt>
   0x0000000000001165 <+28>:    mov    $0x0,%eax
   0x000000000000116a <+33>:    pop    %rbp
   0x000000000000116b <+34>:    ret
End of assembler dump.
(gdb) 
```
