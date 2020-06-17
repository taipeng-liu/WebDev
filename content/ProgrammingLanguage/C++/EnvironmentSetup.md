This post shows you how to setup environment for running C++ code.

## Online Console

* [LeetCode](leetcode.com)<br>
    You may need to sign up an account if you don't have one. Sign in and you will see the icon of "Playground" at top-right. Click on "+" to create a new playground. There is no more setup, so you can go ahead writing your program and click on "Run Code" to compile it.

## Local Setup

* [Visual Studio Code](https://code.visualstudio.com/download) (VS code)<br>

    I highly recommend VS code, because it is light-weighted but still powerful editor. As a fan of `Vim` editor, VS code enables me to write in `Vim` style by installing extensions. There are many awesome extensions you can pluge in to make your styled editor.

* (Optional) Terminal<br>

    If you intend to learn more about system programming, I would recommend you to setup compile environment yourselves and get familiar with writing `Makefile`.<br>

    First, install compiler `g++`. Originally it is called GCC (GNU Compiler Collection) designed for compiling C code. The version supporting C++ is then named G++. 
    
    ```
    $ sudo apt install g++
    ```

    Then install `build-essential`
    
    ```
    $ sudo apt install build-essential
    ```
    
    Confirm installation by checking GCC version:
    
    ```
    $ g++ --version
    ```
    
    Compile your C++ code:
    
    ```
    $ g++ -std=c++0x -o hello main.cpp
    $ ./hello
    Hello, World!
    ```
    
    You can write a `Makefile` to save the compile command. 
    
    ```
    $ vim Makefile
    ```

    Write the following content into `Makefile`, save it and exit:
    
    ```
    CC=/usr/bin/g++
    CC_OPTS=-std=c++0x
    CC_LIBS=
    CC_DEFINES=
    CC_INCLUDES=
    CC_ARGS=${CC_OPTS} ${CC_LIBS} ${CC_DEFINES} ${CC_INCLUDES}

    all: clean hello
    .PHONY=clean

    hello: main.cpp
            @${CC} ${CC_ARGS} -o hello main.cpp

    clean:
            @rm -f *.o
    ```
    
    Okay, now you can type in command `make` to compile your program. Pretty easy, right? Notice that you can use `make clean` to clean your directory by removing all intermediate `.o` files.