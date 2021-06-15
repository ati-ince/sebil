
### **Hide main() function in any C++ program for test purpose**
-----------------------------------------------
**NOT:** I explained in here for **cpp** but if you want to do for **c** language just need to change compiler **g++** to **gcc**.  
 
It is an old question but I think I understand the question you asked.

Yes, as you said, in a project, we need to use more than 1 file like **main.cpp**, **test1.cpp**, and so on, however, we right to have only one '**main()**' function in the project. 

But, when you want to stand-alone test for any cpp file, the compiler prompt " *where is my precious main() or _start() function in this file?* " , the terminal output like:

    /usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/9/../../../x86_64-linux-gnu/Scrt1.o: in function `_start':
    (.text+0x24): undefined reference to `main'
    collect2: error: ld returned 1 exit status

The solution is the usage of **#ifdef / #endif** mechanism. Like below:

A sample project structure: 

[![enter image description here][1]][1]

main.cpp function: 

    #include <iostream>
    
    int main(int argc, char *argv[])
    {
        std::cout << "MAIN" << std::endl;
        return 0;
    }

Our test script, cpp code (vector_test.cpp): 

    #include <iostream>
    
    using namespace std;
    
    int vmain()
    {
        std::cout << "vmain -> ifdef" << std::endl;
        return 0;
    }
    
    #ifdef TESTING
    int main(int argc, char *argv[])
    {
        vmain();
        return 0;
    }
    #endif

So, when you run your project never get any compile-time error because you hide the other main function in the other scripts using #ifdef. 

When you need to test any script, just need to add parameter in compiling like below: 

    $ g++ -DTESTING vector_test.cpp
    $ ./a.out

The output is: 

> vmain -> ifdef

As you see, this approach is similar to the famous **python** 

    def main():
        #do somethings

    if __name__ == "__main__":
       main()

method. 

  [1]: https://i.stack.imgur.com/aV0xd.png
  
-----------------------------------------------
