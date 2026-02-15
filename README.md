

## 📂 Detailed Documentation 

**Documentation**: [ShellFlow Documentation](https://docs.google.com/document/d/1g8XmJmNvYy_WSv75EeGmcLAfnJE6tA3m1OTFraZYogU/edit?tab=t.0#heading=h.43bon5xov91z)  


---


# ShellFlow (my-shell)

A modular Linux-based custom shell implemented in C++ to understand how Unix-like shells manage process creation, execution, and synchronization internally.

---

## Introduction

**my-shell** is a lightweight command-line interpreter built as part of Operating Systems learning. The project demonstrates how a Unix-like shell works internally by implementing core system call interactions and process lifecycle management.

This shell was developed to gain hands-on experience with Linux process handling and system-level programming in C++.

---

## Table of Contents

- [Features](#features)
- [Supported Commands](#supported-commands)
- [Project Structure and Architecture Overview](#project-structure-and-architecture-overview)
- [Requirements](#requirements)
- [Installation and Build](#installation-and-build)
- [Running the Shell](#running-the-shell)
- [Key Concepts Demonstrated](#key-concepts-demonstrated)
- [Limitations](#limitations)
- [Future Improvements](#future-improvements)
- [Learning Outcomes](#learning-outcomes)
- [Contributors](#contributors)
- [License](#license)

---

## Features

- Interactive shell loop  
- Execution of external system commands  
- `PATH`-based command lookup using `execvp()`  
- Parent-child synchronization using `waitpid()`  
- Process state inspection using:
  - `WIFEXITED`
  - `WIFSIGNALED`
  - `WEXITSTATUS`
- Modular architecture  
- Static library generation using `ar`  
- Makefile-based build automation  

---

## Supported Commands

The shell can execute any standalone executable available in the system `PATH`.

### Examples

```bash
ls
pwd
echo Hello
cat file.txt
mkdir test
rm file.txt
grep pattern file.txt
whoami
date
ps
```

Executables located in directories such as `/bin` and `/usr/bin` are supported automatically through `execvp()`.

---

## Project Structure and Architecture Overview

```text
myshell.cpp          - Entry point
lib/
  args               - Argument processing
  dealWithInput      - Input handling
  execute            - Fork and execution control
  childRoutine       - Child process logic
  parentRoutine      - Parent synchronization
  print              - Logging and error handling
Makefile             - Build configuration
```

Header files (`.hpp`) are used to separate interface from implementation.

### 🏗 Architecture Overview

```
           +----------------+
           |   User Input   |
           +----------------+
                    |
                    v
           +----------------+
           | Command Parser |
           +----------------+
                    |
                    v
                fork()
               /      \
              /        \
             v          v
+----------------+  +------------------+
|  Child Process |  |  Parent Process  |
|   execvp()     |  |    waitpid()     |
+----------------+  +------------------+
```


---

## Requirements

- Linux operating system (or WSL on Windows)  
- `g++`  
- `make`  

Install required build tools:

```bash
sudo apt update
sudo apt install build-essential
```

---

## Installation and Build

### Clone the Repository

```bash
git clone <repository-url>
cd my-shell
```

### Compile the Project

```bash
make
```

The build process will:

- Compile source files into object files  
- Create a static library using `ar`  
- Link everything into the final executable `myshell`  

---

## Running the Shell

```bash
./myshell
```

To exit the shell:

```bash
exit
```

or

```bash
quit
```

---

## Key Concepts Demonstrated

- Process creation using `fork()`  
- Process image replacement using `execvp()`  
- Parent-child synchronization via `waitpid()`  
- Copy-on-write memory behavior  
- Process lifecycle monitoring  
- Modular C++ architecture  
- Static library creation  
- Makefile-based build workflow  

---

## Limitations

This shell focuses on core process execution concepts and does not support:

- Built-in commands such as `cd`  
- Pipes (`|`)  
- Redirection (`>`, `<`)  
- Background execution (`&`)  
- Job control  
- Command history  

---

## Future Improvements

- Implement built-in commands (`cd`, `history`)  
- Add support for pipes and redirection  
- Add background process handling  
- Implement signal handling for job control  
- Improve parsing robustness  

---

## Learning Outcomes

This project provided hands-on understanding of:

- Linux system calls  
- Process lifecycle management  
- Execution replacement mechanics  
- Parent-child relationships  
- Build systems and compilation flow  

---

## Contributors

- Aditya

---

## License

This project is intended for educational purposes.


