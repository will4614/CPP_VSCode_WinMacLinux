## C++ in VS Code on Mac, Windows, Linux

## Commands:
F5: Start Debugging (works)

Control-F5: Start without Debugging (works WINDOWS, not working MAC, output shows up in *DEBUG CONSOLE*)
[Not sure if this should work](https://github.com/microsoft/vscode-cpptools/issues/1201)

Control-Shift-B: Build (works)

Terminal | Run task | clean (works, calls *make clean*)

## Mac: 

Use built in gcc/llvm and debugger: 

* BUILD: WORKING 
* DEBUG: WORKING

## Linux: 

Use built in gcc and debugger

* BUILD: WORKING
* DEBUG: WORKING

## Windows: 

current test: using Visual Studio Build Tools (cl, nmake)
* BUILD: WORKING 
* DEBUG: WORKING

Git: [Git For Windows](https://git-scm.com/download/win) Not the Portable Install

* Do you need to install Git strictly AFTER VS Build Tools? Maybe

Which is the easiest compiler tool chain for students to install/use on Windows?

 * cygwin
 * mingw
 * [VS Build Tools](https://visualstudio.microsoft.com/downloads/?q=build+tools#build-tools-for-visual-studio-2022)
   *   Install *Desktop development with C++*
   *   Run VS Code from *Developer Command Prompt for VS 2022*
   *   ~~Select MSVC v142 - VS 2019 C++ ....~~
   *   ~~Select C++/CLI support for v143....~~
 * msys
 * ?
