# Files
**Solution file**  
* CamelCase: HelloWorldSolution

**Project file**  
* CamelCase: HelloWorld

**Source file**  
* snake_case: hello_world.c


# Others
```C
// variable
int table_name; // snake_case

// global variable
int g_table_num // snake_case with "g_" prefix

// constant
const int kDayInWeek = 7; // CamelCase with 'k' prefix

// function
int DeleteUrl(): // PascalCase
    return 0;

// type
struct UrlTablePropertiesStruct; // lowercase and no use '_'
enum eUrlTableErrors // if enum type, use 'e' prefix

enum eResultCode {
    kResultCuccess, // enum value following Constant naming
    kResult_Fail // 예외적으로 enum에서는 '_'를 허용함
};

// Macro
#define PI_ROUNDED (3.0) // UPPERCASE and use '_'
```


# References
https://tttsss77.tistory.com/64
