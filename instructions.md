# Instructions
# 6/5/2023

---

# Download VSCode for Windows

[Link to Download](https://code.visualstudio.com/download)

- Click on Windows 8/10/11

# Things to do after downloading VSCode:

Change your default terminal in
- Ctrl+Shift+` > Dropdown by '+' > Select Default Profilee > Command Prompt

Change your default terminal directory in VSCode
- Ctrl+, > Search for 'CWd' > Change 'Terminal › Integrated: Cwd' to C:\Users\Myles
(Did not want to have to deal with OneDrive anymore)

 
 # Why the system environment PATH is so important

The PATH environment variable is a crucial aspect of command-line use. It enables you to run command-line programs, such as echo and python3 , from any directory without typing the full path.

File execution requires the full path:
- By default, executing any file that you create or download onto your system requires that you specify the full path to that file. 
    - This is a safeguard to prevent you from executing something you don’t intend to execute, because anything that executes on your system has the potential to cause damage if it isn’t used correctly.

What the PATH environment variable does:
- Any operating system (Windows, MacOS, Linux) uses an environment variable called PATH to determine where executable files reside on your system.
- An environment variable is just a named value that can be referenced by your operating environment.
- How to print the PATH:
    - Command Prompt: 
        - set 
    - Powershell: 
        - $env:path.Split(";")
        - $env:path
        - Get-ChildItem
    - Git Bash: 
        - env
        - printenv

# Other Useful Command Line Tools

List all contents of current directory:
- Command Prompt: dir

Save all environment variables into a .txt file:
- Command Prompt: set > env_paths.txt

Update the path so you can
- Example: you have created a directory called /home/local/bin, and put your executable hello.sh in that directory, you could update the PATH in your current terminal session:
    Command Prompt: export PATH=$PATH:/home/local/bin
    - Once that is done, you will be able to execute hello.sh without specifying the full path.

    If you want to permanently add a directory to your PATH, you will have to update it in one of your system initialisation files
    - Careful: If you don’t include the default PATH by including $PATH in your export statement in an initialisation file, you will delete the system directories from the PATH and everything will break!



# Git

1. Navigate to the latest [Git for Windows installer](https://gitforwindows.org/) and download the latest version.
- Once the installer has started, follow the instructions as provided in the Git Setup wizard screen until the installation is complete.
    - Change the 'default branch name' from 'master' to 'main'

1. Ensure that the following are on the path w/ command line: set
- User variables: 
    - None
- System variables:
    - C:\Program Files\Git\cmd
- Open the windows command prompt (or Git Bash if you selected not to use the standard Git Windows Command Prompt during the Git installation).
- More checks:
    - Type 'git version' to verify Git was installed.
        - git version 2.41.0.windows.1
    - where git
        - C:\Program Files\Git\cmd\git.exe

1. Before going back into VSCode, change Git settings globally:
- git config --global user.email mylescgthomas@gmail.com
- git config --global user.name MylesThomas
    - This causes the file located at C:\Users\Myles\.gitconfig to update 

# Python

1. Navigate to the latest [Python Release](https://www.python.org/) and download the latest version.
- Do NOT check the box to add python.exe to the PATH
    - I will deal with this in the next step

- Find the executable (python.exe) on your local and add to system variables's PATH
    - Windows Search Bar > Edit the system environment variables > Environment Variables > System variables > Scroll down to PATH > Edit > Edit > Paste in C:\MinGW\bin > Enter > OK > OK > OK
        - Mine is here: C:\Users\Myles\AppData\Local\Programs\Python\Python311

1. Restart device so that the PATH knows that Python/Pip exist

1. Ensure that the following are on the path w/ command line: set
- User variables: 
    - None
- System variables:
    - python: C:\Users\Myles\AppData\Local\Programs\Python\Python311 
    - pip: C:\Users\Myles\AppData\Local\Programs\Python\Python311\Scripts
- More checks:
    - Python version: python --version
        - Python 3.11.3
    - where python
        - C:\Users\Myles\AppData\Local\Programs\Python\Python311\python.exe
    - Pip version: pip --version or pip -V
        - pip 23.1.2 from C:\Users\Myles\AppData\Local\Programs\Python\Python311\Lib\site-packages\pip (python 3.11)
    - Pip location: 
        - C:\Users\Myles\AppData\Local\Programs\Python\Python311\Scripts\pip.exe
    
1. Install Extensions in VSCode:
- Ctrl-Shift-X to get into Extensions
    Packages we want to download: 
    - Python Extension Pack

1. Test out a 'Hello World' Example

``` python
if __name__ == "__main__":
    num = int(input("Enter the number of which the user wants to print the multiplication table: "))            
    print("The Multiplication Table of: ", num)    
    for count in range(1, 10 + 1):      
        print(num, 'x', count, '=', num * count)  
```

- Save into a Python Script (.py) in C:\Users\Myles
- Open command prompt: 
    - python program.py

Note: tldr; the first line of code allows you to execute code when the file runs as a script, but not when it is imported as a module

What happens when you run a Python Script: 
- In Python, the interpreter will read your code line by line and execute it in a call stack.
- The python default implementation is written in C programming (CPython), so when you import libraries into Python you are running C code under the hood.
    - While in C, the compiler will check grammar, translate to assembly code, then compile and link them together to binary machine code.

# R
1. Install R: [Link](https://cran.r-project.org/bin/windows/base/)
- 'Download R-4.3.0 for Windows'
    - It will end up here: C:\Program Files\R\R-4.3.0
- Add the location of R.exe to PATH:
    - Mine is here: C:\Program Files\R\R-4.3.0\bin

1. Install Rtools: [Link](https://cran.r-project.org/bin/windows/Rtools/)
- 'Rtools43 installer'
    - It will end up here: C:\rtools43.
- Add the location of Rtools.exe to PATH:
    - The downloader should automatically put this into PATH: 
        - You may not need this actually.........Mine is here: C:\Program Files\R\R-4.3.0\bin

1. Install RStudio: [Link](https://posit.co/download/rstudio-desktop/)
- 'DOWNLOAD RSTUDIO DESKTOP FOR WINDOWS'
    - It will end up here: C:\Program Files\RStudio


1. Restart device so that the PATH knows that R and Rtools are in the PATH


1. Ensure that the following are on the path w/ command line: set
- User variables: 
    - None
- System variables:
    - C:\Program Files\R\R-4.3.0\bin
- More checks:
    - Check version of R: 
        - Command Prompt: R --version
        - R/RStudio: R.version
    - Check location of R: 
        - Command Prompt: where R
            - If this doesn't work, then R is not on the PATH...
        - R/RStudio: file.path(R.home("bin"), "R")
            - I don't like this as much
    - Check where Rtools is (make.exe): 
        - Command Prompt: 
        - R/RStudio: 

More...

    - Download devtools in R: install.packages("devtools")
        - This won't work if Rtools is improperly downloaded
    - Verify Rtools installation in R/RStudio: pkgbuild::find_rtools()
    

# Java

1. Download the [Latest LTS Release of the Java Development Kit (JDK)](https://adoptium.net/)
- Necessary for developing Java applications and applets
    - As a developer, the Java Runtime Environment (JRE) is necessary as well, but luckily it comes with the JDK.

1. Restart device so that the PATH knows that JDK exists

1. Ensure that the following are on the path w/ command line: set
- User variables: 
    - None
- System variables:
    - C:\Program Files\Eclipse Adoptium\jdk-17.0.7.7-hotspot\bin
- More checks:
    - JRE availability check: java -version
        - openjdk version "17.0.7" 2023-04-18
    - Availability check for JDK: javac -version
        - javac 17.0.7

1. Install Extensions in VSCode:
- Ctrl-Shift-X to get into Extensions
    Packages we want to download: 
    - Extension Pack for Java

1. Test out a [Simple Example:](https://en.wikibooks.org/wiki/Java_Programming/Understanding_a_Java_Program)

``` java
import java.util.*;
public class Distance {
   private java.awt.Point point0, point1;
 
   public Distance(int x0, int y0, int x1, int y1) {
     point0 = new java.awt.Point(x0, y0);
     point1 = new java.awt.Point(x1, y1);
   }
 
   public void printDistance() {
     System.out.println("Distance between " + point0 + " and " + point1
                     + " is " + point0.distance(point1));
   }
 
   public static void main(String[] args) {
     Distance dist = new Distance(
              intValue(args[0]), intValue(args[1]),
              intValue(args[2]), intValue(args[3]));
     dist.printDistance();
   }
 
   private static int intValue(String data) {
     return Integer.parseInt(data);
   }
 }
```

- Save into a Java Source File (.java) file in C:\Users\Myles
    - The above program would be saved as Distance.java ie. the name of your file should be the same as the name of your class definition and followed by the .java extension
        - Note: This name is case-sensitive
- Open command prompt:
    - Compile the java source file: javac Distance.java
        - This is necessary. This reads class and interface definitions and compiles your source code into bytecode
            - Bytecode: platform-independent instructions for the Java VM
            - If there are no errors in your code, the command prompt will take you to the next line
    - Run your application: java Distance 0 3 4 0
        - This converts the Java byte codes to platform-dependent machine codes so your computer can understand and run the program.
        - The output should read the following:
            - Distance between java.awt.Point[x=0,y=3] and java.awt.Point[x=4,y=0] is 5.0
            - If you tried again with java Distance -4 5 11 19, you'd get this:
                - Distance between java.awt.Point[x=-4,y=5] and java.awt.Point[x=11,y=19] is 20.518284528683193

Notes: 
- This class belongs to an unnamed package. More on this [here:](https://en.wikibooks.org/wiki/Java_Programming/Packages)
- You will also find a CLASS file (Distance.class) in your working directory once you compile
    - This is the class file produced by a Java compiler from Java programming language source files (.java files) containing Java classes
        - When you compile the java source code and it turns your source code into bytecode
        - If a source file has more than one class, each class is compiled into a separate class file.
            - This program has 1 public class, so only 1 CLASS file is created


# C++

1. Download the [Minimalist GNU for Windows (MinGW) and GCC Compiler](https://sourceforge.net/projects/mingw/)
- Keep Installation Directory as C:\MinGW > Continue
- When 'MinGW Installation Manager' Opens: 
    - There are 7 packages in 'Basic Setup', right click them all and 'Mark for installation'
        - Top left corner > Installation > Apply Changes > Apply

- Close down MinGW Installation Manager
- Restart device so that the PATH knows that MinGW exists

Notes on MinGW: 
- MinGW: A native Windows port of the GNU Compiler Collection (GCC), with freely distributable import libraries and header files for building native Windows applications; includes extensions to the MSVC runtime to support C99 functionality. 
    - All of MinGW's software will execute on the 64bit Windows platforms.

1. Ensure that the following are on the path w/ command line: set
- User variables: 
    - None
- System variables:
    - C:\MinGW\bin
- More checks:set
    - Check which version of C compiler is installed on machine: 
        - gcc –v or gcc –-version
    - More checks from [VSCode article](https://code.visualstudio.com/docs/cpp/config-mingw):
        - gcc --version
        - g++ --version
        - gdb --version

Notes:
- If the system variable is not there, here's how you can append it: 
    - Windows Search Bar > Edit the system environment variables > Environment Variables > System variables > Scroll down to PATH > Edit > Edit > Paste in C:\MinGW\bin > Enter > OK > OK > OK
        - Another way is via Command Line, but that is more risky and can cause everything to break.

- If you don't see the expected output or g++ or gdb is not a recognized command, make sure your PATH entry matches the Mingw-w64 binary location where the compilers are located. If the compilers do not exist at that PATH entry, make sure you followed the instructions on the MSYS2 website to install Mingw-w64.
- If gcc has the correct output but not gdb, then you need to install the packages you are missing from the Mingw-w64 toolset.


1. Install Extensions in VSCode:
- Ctrl-Shift-X to get into Extensions
    Packages we want to download: 
    - C/C++
    - C/C++ Extension Pack
    - Code Runner

1. Test out a [Simple Example:](https://en.wikibooks.org/wiki/Java_Programming/Understanding_a_Java_Program)

## Method #1: Compile a Single File Program (Easiest way - Compiling into an executable)

``` cpp
// Computes time difference of two time period
// Time periods are entered by the user

#include <iostream>
using namespace std;

struct TIME
{
  int seconds;
  int minutes;
  int hours;
};

void computeTimeDifference(struct TIME, struct TIME, struct TIME *);

int main()
{
    struct TIME t1, t2, difference;

    cout << "Enter start time." << endl;
    cout << "Enter hours, minutes and seconds respectively: ";
    cin >> t1.hours >> t1.minutes >> t1.seconds;

    cout << "Enter stop time." << endl;
    cout << "Enter hours, minutes and seconds respectively: ";
    cin >> t2.hours >> t2.minutes >> t2.seconds;

    computeTimeDifference(t1, t2, &difference);

    cout << endl << "TIME DIFFERENCE: " << t1.hours << ":" << t1.minutes << ":" << t1.seconds;
    cout << " - " << t2.hours << ":" << t2.minutes << ":" << t2.seconds;
    cout << " = " << difference.hours << ":" << difference.minutes << ":" << difference.seconds;
    return 0;
}
void computeTimeDifference(struct TIME t1, struct TIME t2, struct TIME *difference){
    
    if(t2.seconds > t1.seconds)
    {
        --t1.minutes;
        t1.seconds += 60;
    }

    difference->seconds = t1.seconds - t2.seconds;
    if(t2.minutes > t1.minutes)
    {
        --t1.hours;
        t1.minutes += 60;
    }
    difference->minutes = t1.minutes-t2.minutes;
    difference->hours = t1.hours-t2.hours;
}
```

Steps:

1. Save into a C++ Source File (.cpp) in C:\Users\Myles
    - The above program can be saved as Program.cpp
        - Unlike Java, you do not need to match filename with the Program class

2. Compile the C++ Source File: 
- Default Compilation: g++ Program.cpp
    - Formula: g++ `<filename>` 
    - This compiles a file named "filename" into an executable named "a.exe"
- Run the executable: a

Note: This compiling of the C++ Soure File is necessary. 
- Computers can only understand machine code
    - The C++ Source file is not machine code, it is source code
        - By compiling C++ code, the source code is translated into machine code that the computer can understand and execute.

3. Run the executable
- Command prompt: a or a.exe

Optional:

While compiling the C++ Source File, you can rename the executable to be something more intuitive than a.exe:
- Default Compilation w/ Renaming the Output: g++ -o nameOfCppApplication Program.cpp
    - Formula: g++ -o `<execname> <filename>` 
    - This compiles a file named "filename" into an executable named execname
        - The '-o' argument will let you rename the output into something much more intuitive

- Run the executable
- Command prompt: nameOfCppApplication or nameOfCppApplication.exe




Note: Delete the following before continuing:
- a.exe
- nameOfCppApplication.exe

## Method #2: Compile a Single File Program (Medium way - Linking Object code with precompiled pieces of code)

1. Save into a C++ Source File (.cpp) in C:\Users\Myles
    - The above program can be saved as Program.cpp

2. Creating Object Code: 
- Command Prompt: g++ -c Program.cpp
    - This creates object code, in the form of an 'O file' named 'Program.o'
        - O file: An object file is a computer file containing object code, that is, machine code output of an assembler or compiler.
        - Object Code: source code that has been compiled down to machine language (binary) but has not yet been linked with all the libraries and other files.
            - This is a single file example, so the linking step is not nearly as important

3. Linking Object Code:
Once object code has been created, an executable can be created by linking the object code with other precompiled pieces of code (other ".o" files, but there are none in this example)

Note: All the standard libraries have object code compiled for them

- Command Prompt: g++ -o myExecutableMethodTwo Program.o
    - Formula: g++ -o `execname` filename.o
    This does 2 things:
    1. Link the object code `Program.o` with any of its libraries 
    2. Creates an executable named `myExecutableMethodTwo`

4. Linking External Libraries
This example doesn't have any - if you'd like to see this in action, continue onto the next method

5. Run the executable
- myExecutableMethodTwo

It should behave just as before in Method #1.
- Make sure to delete this file once you are able to execute the program

If you'd like to learn how to turn this into a multi-file program and then compile, the continue on.


## Method #3: Compile a Multi-File Program (Best practice)

Most coding projects will involve multiple files.
- For larger projects, you will want to split your code into header files (.h) and source code files.
    - This will allow you to re-use your classes in multiple projects.
    - It will cut down on compile time because potentially only some of the files need to be re-compiled.

xxxx




When working with multiple files the question of how to include properly files always comes up.

### Basic Hello World Example: 

``` cpp
// 2 ways
 #include <file1.h>    // (1)
#include "file.cpp"    // (2)
```

- You are used to seeing style (1) used for standard libraries.
    - In early programming courses, often students use style (2) for their own files. 
    - For this manual, we will use style (1). 

- To make this style work the way you intend it to, you must tell the compiler where to look for the "include" files. 
    - This is where the '-I' flag comes in. 
        - Anything that follows immediately after the '-I', no spaces, will be searched. 
        - If you need to search more than one directory, simply use multiple '-I' statements.

Try compiling the following multi-file program.
- It is assumed that these files have been created in VSCode and are in the current working directory. 

``` cpp
// file1.h
const int magic_number = 1492;
long multiply_by_MN(int number);
```

``` cpp
// file1.cpp
#include <file1.h>
long multiply_by_MN(int number) {
  return number * magic_number;
}
```

``` cpp
// main.h
const int loop_n_times = 4; // i changed it from 'constant' to 'const', I believe that was just an error/type by the instructor
```

``` cpp
// main.cpp
#include <iostream> // note: I personally changed this from iostream.h to iostream (I don't have a iostream.h header file in C:\Users\Myles !)
#include <file1.h>
#include <main.h>
using namespace std; // Added this myself too
int main() {
  int sum = 0;
  for (int i = 0; i < loop_n_times; i++) {
    sum += mulitply_by_MN (13);
  }
  cout << "Final number is" << sum << "\n";
  return 0;
}
```

1. Write each block of code into its respective file:
- file1.h
- file1.cpp
- main.h
- main.cpp

Make sure to put each in a directory and open VSCode to that folder.

Note on we why need Headers:
- Every C++ program needs at least one header file to be meaningful. 
    For example, most C++ programs need the cin object to take input from the user and much other pre-written code, which helps to make programming easier, so to use such functionalities, you need a header file.
    - .h file contains shared declarations
    - .cpp file contains definitions and local declarations.
        - It's important that you understand the difference between declarations and definitions.


1. Compile file1.cpp into machine executable Object Code:

- Command Prompt: g++ -c -I. file1.cpp

    - Make sure to tell the compiler where to look for header files w/ the I-flag: 

        - Fixes the error for can't open source file "file.h"

            - The dot after -I means 'here' ie. C:\Users\Myles

            - It tells the compiler where to find the file (more specifically, header files)

        As default, here are the rules:

        - When you use the `" "`'s to include a file, the compiler looks in the current directory to find the files.
            - Basically you're telling the compiler where to find the file. 
            - Usually: It's because it is a user-defined header file

        - When you use the <>'s to include a file, the compiler searches all the places it expects to find include files. 
        (But it doesn't search your current directory by default.) That's why you get the error message. 
            - Usually Standard library header files
        
        - To solve this problem, use the '-I' flag like this: g++ -c -I. file.cpp. 
            - Now when you do 'dir'call, you see the 'file.o' file.

        - Now, compile 'main.cpp' the same way, g++ -c -I. main.cpp. To create the executable, link the pieces together and name the output, g++ -o sample main.o file.o. This creates an executable named 'sample'. Try running it by typing sample at the command prompt.


You should now see 'file1.o' in the directory before continuing.

1. Compile main.cpp the same way:
- Command Prompt: g++ -c -I. main.cpp

You should now see 'file1.o' in the directory before continuing.

1. Create the executable
- Link the pieces together and name the output: g++ -o myDoubleFileExecutable main.o file1.o
    - This creates an executable named 'myDoubleFileExecutable.exe'.

1. Run the executable
- Command Prompt: myDoubleFileExecutable or myDoubleFileExecutable.exe

Optional Practice/Understanding:

1. Change a .cpp file:

I will change main.cpp:

``` cpp
/*sum += =;*/
sum += 1000;
```

1. Re-compile main.cpp: g++ -c -I. main.cpp

1. Finish by re-linking and running the executable:
- g++ -o myDoubleFileExecutable main.o file1.o
- 

Explanation for benefit of using .o files:
If you change a .cpp file,  you need only recompile it and then relink all the pieces.
- There is no need to recompile 'main.cpp'. 
    - This is the benefit of using .o files.

Finally, be wary of using 'test' or 'exec' as the name of your executable. 
- There are standard unix commands that already have these names. They will be called instead of the ones you created. 
    - Use ./`<filename>` to be safe.

Remember before starting:

You can't translate .h files to object or executable code. 
- These are header files used to inform the compiler how to interpret and translate the code in a .cpp file. (An exception is when the file contains template code. Then the header file contains the implementation, so there is no .cpp file. Even in this case, however, you can't make workable object code from the header file.)
- Compiling the object code would require a statement like g++ -c file.cpp, but that causes the error statement: "file1.cpp:2: file1.h: No such file or directory"

,,,Why did this happen? When you use the " "'s to include a file, the compiler looks in the current directory to find the files. Basically you're telling the compiler where to find the file. When you use the <>'s to include a file, the compiler searches all the places it expects to find include files. But it doesn't search your current directory by default. That's why you get the error message. To solve this problem, use the '-I' flag like this: g++ -c -I. file.cpp. Now when you do an ls you see the 'file.o' file.

2. 

Steps: 

- 


,,,,,,

Notes: 
- [Compiling a Single File Program] (https://www.cs.fsu.edu/~lacher/lectures/Output/compiler/index.html?$$$compiler2.html$$$)

- [Compiling a Multi-File Program] (https://www.cs.fsu.edu/~lacher/lectures/Output/compiler/index.html?$$$compiler2.html$$$)


- [cpp vs. hpp](https://stackoverflow.com/questions/5171502/c-vs-cc-vs-cpp-vs-hpp-vs-h-vs-cxx):
    - .cpp: C++ Source Code
    - .hpp: Header files, for C/C++
        - Usually only contains 'declarations'
            - [Declaration](https://learn.microsoft.com/en-us/cpp/cpp/declarations-and-definitions-cpp?view=msvc-170):  
                - A C++ program consists of various entities such as variables, functions, types, and namespaces. 
                - Each of these entities must be declared before they can be used. A declaration specifies a unique name for the entity, along with information about its type and other characteristics. 
                    - In C++ the point at which a name is declared is the point at which it becomes visible to the compiler. 
                        - You can't refer to a function or class that is declared at some later point in the compilation unit.
                        - Variables should be declared as close as possible before the point at which they're used.

- "Why would I ever want to create object code? It's clearly simpler to go straight to an executable." 
    - That's a good question. If you're only creating an executable from a single file, there isn't any reason to make object code.
- But, most projects in this course will involve multiple files. 
    - By creating object code, you can create a mini library of code that need not be recompiled every time you want to make a change to only one file. All you need to do is change one file, and then compile it and link them together.

# Node.JS

1. Navigate to [nodejs.org](https://nodejs.org/en) and download the 18.16.0 LTS
- Check box to automatically download necessary tools

1. Restart VSCode after this

1. Ensure that the following are on the path w/ command line: set
- User variables: 
    - None
- System variables:
    - C:\Program Files\nodejs\
    - C:\ProgramData\chocolatey\bin
- More checks:
    - Find location of node.: node --version or node -v
        - v18.16.0

1. Create a package 
- Change into directory: cd `directory name`
- Init w/ automatic yes's: npm init -y

# 