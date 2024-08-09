```C
// hello_world.c
#include <stdio.h> // standard input&output header file

int main(void) { // return_value is integer, parameter is void
    printf("Hello, World!"); // Output: Hello, World!

    return 0;
```
* * *
> 다음 코드와 같이 `#include <stdio.h>`를 comment하면 error가 발생한다.  
이유는 `printf()`는 stdio.h header file에서 define된 function이기 때문.

```C
// hello_world.c
//#include <stdio.h>

int main(void) {
    printf("Hello, World!"); // Error occured.

    return 0;
```

```cmd
REM LINK 과정에서 unresolved externeals error occured
Build started...
1>------ Build started: Project: HelloWorld, Configuration: Debug Win32 ------
1>hello_world.c
1>C:\C-Overview\HelloWorldSolution\HelloWorld\hello_world.c(4,11): warning C4013: 'printf' undefined; assuming extern returning int
1>hello_world.obj : error LNK2019: unresolved external symbol _printf referenced in function _main
1>C:\C-Overview\HelloWorldSolution\Debug\HelloWorld.exe : fatal error LNK1120: 1 unresolved externals
1>Done building project "HelloWorld.vcxproj" -- FAILED.
========== Build: 0 succeeded, 1 failed, 0 up-to-date, 0 skipped ==========
```
