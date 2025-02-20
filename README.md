# 42_Tools
Few links and configs to help me through my journey at 42 School

---
### Content Table:
* **[Vim](#vim)**
* **[Github Links](#github-links)**
* **[Commit to new Repo](#commit-to-new-repo)**
* **[Detect memory leaks](#detect-memory-leaks)**
* **[Debugging](#debugging)**
* **[VS Code Debug](#vs-code-debug)**
* **[Learn more](#learn-more)**
* **[Algorithm Study List](#algorithm-study-list)**
---
## Vim
### - Personal Config
```
" For exams
set nu
syntax on
set mouse=a
set noswapfile
set tabstop=4
set shiftwidth=4
set autoindent
set smartindent
inoremap ( ()<left>
inoremap [ []<left>
inoremap { {}<left>
inoremap ' ''<left>
inoremap " ""<left>

" Quality of life
set showmatch
set ruler
set colorcolumn=80
hi colorcolumn ctermbg=180
set list
set listchars=tab:\>\ ,eol:$
```
---
### - Shortcuts
If feeling rusty: [Vim genius](http://www.vimgenius.com/)
- `Ctrl + Z` Get back to shell
- `fg` Get back to vim
- `i` Insert at cursor
- `I` Insert at start of line
- `o` Insert mode line below
- `O` Insert mode line above
- `A` Append at eol
- `0` Go to beginning of line
- `$` Go to eol
- `^` Go to start of first string
- `w` Jump to beginning of next word
- `b` Go back to beginning of previous word
- `e` Jump to end of next word
- `u` Undo
- `Ctrl + r` Redo
- `yy` Copy
- `p` Paste
- `dd` Delete line
- `dw` Delete word
- `x` Delete char
- `r` Replace char
- `:%s/foo/bar/g` Search and replace
---

## Github Links
[42 Tips and Tricks](https://github.com/ricardoreves/42-tips-and-tricks)

[42tools](https://github.com/solareenlo/42tools)

[The Algorithms](https://github.com/TheAlgorithms)

[42stud](https://stud42.fr/)

[42-algorithm](https://github.com/dev-jko/42-algorithm)

[awesome-42](https://github.com/leeoocca/awesome-42)

[42-Tests](https://github.com/Kwevan/42-Tests)

---
## Commit to new Repo
The proper way to push a new project into an existing GitHub repository follows these steps:

- Create a GitHub repository for the existing project.
- Copy the GitHub URL for the new repo to the clipboard.
- Perform a git init command in the root folder of the existing project.
- Add all of the existing project’s files to the Git index and then commit.
- Add the GitHub repo as a remote reference for the existing project.
- Perform a git push operation with the -u and -f switches.
- Verify that the existing project’s files have been pushed to GitHub.
---
These commands assume a push to a GitHub repo named existing-website, owned by a GitHub user named cameronmcnz:
- git init
- git add .
- git commit -m "Add existing project files to Git"
- git remote add origin https://github.com/cameronmcnz/example-website.git
- git push -u -f origin master

---
## Detect memory leaks
### GCC
```
gcc -g3 -fsanitize=address
```

### Diff
On Unix-like operating systems, the diff command analyzes two files and prints the lines that are different. In essence, it outputs a set of instructions for how to change one file to make it identical to the second file.
```
diff -u file1.txt file2.txt
```
- [source](https://www.computerhope.com/unix/udiff.htm)

### Valgrind
1. Install
```
sudo apt install valgrind  # Ubuntu, Debian, etc.
sudo yum install valgrind  # RHEL, CentOS, Fedora, etc.
sudo pacman -Syu valgrind  # Arch, Manjaro, Garuda, etc
```
2. Usage
```
valgrind --leak-check=full \
         --show-leak-kinds=all \
         --track-origins=yes \
         --verbose \
         --log-file=valgrind-out.txt \
         ./executable exampleParam1
```
---
## Debugging
### LLDB
#### Usage
0. Compile `gcc -g main.c`-o <prog>
1. Launch lldb `lldb <prog> <arg1> <arg2>`
2. Set breakpoint `b <funct_name>`
3. Launch the executable in the debugger `run`
- Some helpful commands
```
  expression      -- Evaluate an expression on the current thread.  Displays
                       any returned value with LLDB's default formatting.
  frame           -- Commands for selecting and examing the current thread's
  gui             -- Switch into the curses based GUI mode.
  help            -- Show a list of all debugger commands, or give details
                       about a specific command.
  target          -- Commands for operating on debugger targets.
  
  b         -- Set a breakpoint using one of several shorthand formats.
  bt        -- Show the current thread's call stack.  Any numeric argument
               displays at most that many frames.  The argument 'all' displays
               all threads.  Use 'settings set frame-format' to customize the
               printing of individual frames and 'settings set thread-format'
               to customize the thread header.
  c         -- Continue execution of all threads in the current process.
  display   -- Evaluate an expression at every stop (see 'help target
               stop-hook'.)
  j         -- Set the program counter to a new address.
  kill      -- Terminate the current target process.
  l         -- List relevant source code using one of several shorthand formats.
  n         -- Source level single step, stepping over calls.  Defaults to
  p         -- Evaluate an expression on the current thread.  Displays any
               returned value with LLDB's default formatting.
  q         -- Quit the LLDB debugger.
  r         -- Launch the executable in the debugger.
  s         -- Source level single step, stepping into calls.  Defaults to
  v         -- Show variables for the current stack frame. Defaults to all
               arguments and local variables in scope. Names of argument,
               local, file static and file global variables can be specified.
               Children of aggregate variables can be specified such as
               'var->child.x'.  The -> and [] operators in 'frame variable' do
               not invoke operator overloads if they exist, but directly access
               the specified element.  If you want to trigger operator
               overloads use the expression command to print the variable
               instead.
               It is worth noting that except for overloaded operators, when
               printing local variables 'expr local_var' and 'frame var
               local_var' produce the same results.  However, 'frame variable'
               is more efficient, since it uses debug information and memory
               reads directly, rather than parsing and evaluating an
               expression, which may even involve JITing and running code in
               the target program.

```
---
## VS Code Debug
- [gourav.io](https://gourav.io/blog/setup-vscode-to-run-debug-c-cpp-code)

### VS Code
- [debugging](https://code.visualstudio.com/docs/editor/debugging)

### Clang-format
- [How to set up clang-format in Visual Studio Code in a Vagrant environment](https://eellaup.medium.com/how-to-set-up-clang-format-in-visual-studio-code-in-a-vagrant-environment-georgiatech-gios-1935ed73efd1)
---
## Learn more
- [Learn the lldb debugger basics in 11 minutes](https://www.youtube.com/watch?v=v_C1cvo1biI)
- [GDB to LLDB command map](https://lldb.llvm.org/use/map.html)
- [How to find Segmentation Error in C & C++ ? (Using GDB)](https://www.geeksforgeeks.org/how-to-find-segmentation-error-in-c-c-using-gdb/?ref=lbp)
- [Pony LLDB Cheat Sheet](https://www.ponylang.io/reference/pony-lldb-cheatsheet/)
- [How to use the GDB debugger - basics](https://www.cs.fsu.edu/~myers/cop3330/debug/debugger.html)
---
## Algorithm Study List
- Dynamic memory allocation in C (7.5 h)</br>
         - Data representation in memory</br>
         - Pointers (or references to objects)</br>
         - Runtime memory management (dynamic memory allocation)</br>
- Static and dynamic linear Abstract Data Types (ADT, 9.0 h)</br>
         - Simple and multiple linked structures</br>
         - Stack and queues</br>
         - Strategies for data structure selection</br>
- Recursion and recursive programs (12.0 h)</br>
         - The notion of recursion and the divide-and-conquer paradigm</br>
         - Mathematical recursive functions</br>
         - Simple recursive procedures</br>
         - Recursive sorting (mergesort, quicksort, heapsort)</br>
         - Backtrack and implementation of recursion</br>
         - Combinatorics principle and their implementation</br>
- Modularity and modular implementation of algorithms and data structures (4.5 h)</br>
         - The implementation-interface-client model</br>
         - Implementation in C of programs with multiple source and header files</br>
         - Basic use of development and debug tools, like make and gdb</br>
- Abstract objects, collections of objects, and ADTs (7.5 h)</br>
         - Classification, definition, and examples</br>
         - Trees</br>
         - Binary search trees</br>
         - Hash tables</br>
         - Priority queues, heaps, and heap-sort</br>
- Greedy algorithm (1.5 h)</br>
- Dynamic programming (1.5 h)</br>
- Graph theory (7.5 h)</br>
         - Graph representation</br>
         - Visits (depth-first and breadth-first search) and their applications</br>
         - Single-source shortest paths</br>
         - Minimum spanning trees</br>
- Problem-solving and practice (8.0 h)</br>
         - Analysis and definition of strategies for data structures and algorithms</br>
         - Search and optimization problems</br>
         - Techniques to explore the state space based on combinatorics</br>

[MIT Intro to Algorithms](https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-spring-2020/download/)
[MIT Introduction to Algorithms](https://www.youtube.com/playlist?list=PLUl4u3cNGP61Oq3tWYp6V_F-5jb5L2iHb)
[MIT Design and Analysis of Algorithms](https://www.youtube.com/playlist?list=PLUl4u3cNGP6317WaSNfmCvGym2ucw3oGp)
[MIT Performance Engineering of Software Systems](https://www.youtube.com/playlist?list=PLUl4u3cNGP63VIBQVWguXxZZi0566y7Wf)
[MIT Math for CS](https://ocw.mit.edu/courses/6-042j-mathematics-for-computer-science-fall-2010/download/)
[Tim Roughgarden Series](https://timroughgarden.org/videos.html)
[Steven Skiena Youtube](https://www.youtube.com/watch?v=A2bFN3MyNDA)
