## C++ in VS Code on Mac, Windows, Linux

### Make sure your set the platform correctly on the bottom right of the VS Code window.

## Commands:
F5: Start Debugging (works)

Control-F5: Start without Debugging (works WINDOWS, not working MAC, output shows up in *DEBUG CONSOLE*)

[Not sure if *Start without Debugging* should work](https://github.com/microsoft/vscode-cpptools/issues/1201)

Control-Shift-B: Build (works)

Terminal | Run task | clean (works, calls *make clean*)

## Mac: 

Use built in gcc/llvm and debugger: 

* BUILD: WORKING 
* DEBUG: WORKING
* Need to install https://github.com/vadimcn/vscode-lldb
* stopAtEntry not working, set your own breakpoint in main()
* [Freezes on Mac?](https://github.com/microsoft/vscode/issues/145387)
* [lldb-mi occasionally freezes on Mac](https://github.com/microsoft/vscode-cpptools/issues/7240)

## Linux: 

Use built in gcc and debugger

* BUILD: WORKING
* DEBUG: WORKING
* If you want to use clang++ on linux make sure you have [libstdc++ installed correctly.](https://stackoverflow.com/a/66163184)
* gdb on Linux won't step into functions/run in functions [reliably](https://github.com/microsoft/vscode-cpptools/issues/3648)

## Windows: 

current test: using Visual Studio Build Tools (cl, nmake)
* BUILD: WORKING 
* DEBUG: WORKING
* Set up debug console correctly : https://github.com/microsoft/vscode-cpptools/pull/6794
* ```lauch.json```: ```"console": "integratedTerminal",```  Works on all platforms.
* If the VS Build Tools are installed in Program Files x86, edit ```intelliSenseMode``` in c_cpp_properties.json to be ```windows-msvc-x86```

Git: [Git For Windows](https://git-scm.com/download/win) Not the Portable Install

* Do you need to install Git strictly AFTER VS Build Tools? Maybe

Which is the easiest compiler tool chain for students to install/use on Windows?

 * cygwin
 * mingw
 * [VS Build Tools](https://visualstudio.microsoft.com/downloads/?q=build+tools#build-tools-for-visual-studio-2022)
   *   Install *Desktop development with C++*
   *   Run VS Code from *Developer Command Prompt for VS 2022*
   *   OR: [Run VS Code Outside of the Developer Command Prompt](https://code.visualstudio.com/docs/cpp/config-msvc#_run-vs-code-outside-the-developer-command-prompt)
   *   ~~Select MSVC v142 - VS 2019 C++ ....~~
   *   ~~Select C++/CLI support for v143....~~
 * msys
 * ?

## Codespaces
* This repository contains a custom container that installs enscript and ghostscript to easily print source code
* Students can run ```make -f Makefile_linux printAll``` to print the code to bin/src.pdf. 
* Students can then Right Click on src.pdf and download the PDF locally

## Notes
* [View pointer as array in debugger](https://github.com/microsoft/vscode-cpptools/issues/172#issuecomment-1281804128)
  *   For LLDB:
	  * `/nat *(int(*)[13])pIntArray`
  *   For GDB:
      * `*pIntArray@13` or  `*pIntArray@ARRAY_SIZE`
* [Using expressions in the watch panel with LLDB](https://github.com/vadimcn/vscode-lldb/blob/master/MANUAL.md#native-expressions)
* [lldb should debug gcc compiled code](https://aaronbloomfield.github.io/pdr/docs/gdb_vs_lldb.html)
* [vscode-cpptools](https://github.com/microsoft/vscode-cpptools#quick-links)
* [C++ on Windows](https://code.visualstudio.com/docs/cpp/config-msvc)
* [Using CLANG](https://code.visualstudio.com/docs/cpp/config-clang-mac)
* [Run Without Debugging](https://github.com/microsoft/vscode-cpptools/issues/1201)
* [Setup VS Code for C++ (iffy)](https://gourav.io/blog/setup-vscode-to-run-debug-c-cpp-code)
* [Debugging in VS Code](https://code.visualstudio.com/docs/editor/debugging)
* [Configuring Debugging](https://code.visualstudio.com/docs/cpp/launch-json-reference)
* [Launch.json schema](https://docs.microsoft.com/en-us/cpp/build/launch-vs-schema-reference-cpp?view=msvc-170)
* [tasks.json schema](https://code.visualstudio.com/docs/editor/tasks-appendix)
* [MinGW](https://code.visualstudio.com/docs/cpp/config-mingw)
* [External tools and tasks](https://code.visualstudio.com/docs/editor/tasks)
* [C++20 in Visual Studio Compiler](https://devblogs.microsoft.com/cppblog/msvc-cpp20-and-the-std-cpp20-switch/)
* [Configure default terminal in VS Code](https://code.visualstudio.com/docs/terminal/profiles)
* [Working example of Configure default terminal in VS Code. Set args like in tasks.json to invoke VSDevCmd.bat](https://github.com/microsoft/vscode/issues/122355#issuecomment-833086902)
* [Print Extension](https://github.com/PDConSec/vsc-print/blob/master/doc/manual.eng.md)

## Git
* [Set local .gitconfig per directory](https://stackoverflow.com/questions/21307793/set-git-config-values-for-all-child-folders/48088291#48088291)
* [Use two GitHub accounts/SSH Keys on one computer](https://gist.github.com/aprilmintacpineda/f101bf5fd34f1e6664497cf4b9b9345f))

## [Key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_default-keybindings)

You can use key bindings to provide the not working Ctrl-F5 Start without Debugging feature:

keybindings.json:
```
  {
    "key": "Ctrl+F5",
    "command": "workbench.action.tasks.runTask",
    "args": "runMe",
    "when": "!inDebugMode"
  }
  ```
  
  Create a *runMe* task in *[tasks.json](.vscode/tasks.json#L72)* which calls the correct [Makefile](Makefile_linux#L29) to build and run the executable. 
  
  Note that keybindings are a *per user* setting, not a per project setting.
