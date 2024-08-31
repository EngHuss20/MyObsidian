#### Review
---
- user space --> libC --> system call --> stacks (Linux Arch)
- search [[system v]] & [[system d]] (the two types of init process)


#### Questions_from_record:
---
- What is the diff bet invoking a function and calling it? search for it
- **Hazem: el filesystem stack bey ADD system calls !! 
- File of interaction wasn't clear----------------X
---
## session:
---
- Sys call is a wrapper on a SW interrupt which main function is to communicate with the kernel
- Entry point of the [[kernel]] is the actual function that makes the action
- **Basically the glibc makes a system call with a specific number which choose a specific SystemCallEntryPoint(a pointer to function in a specific stack in the kernel)
- 