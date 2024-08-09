```C
// sizeof.c
#include <stdio.h>

int main(void) {
    int i = 1;
    char c = 'a';
    float f = 1.1;
    double d = 1.1;
    
    printf("%d\n", sizeof(i)); // Output: 4 // byte
    printf("%d\n", sizeof(c)); // Output: 1 // byte
    printf("%d\n", sizeof(f)); // Output: 4 // byte
    printf("%d\n", sizeof(d)); // Output: 8 // byte

    return 0;
}
```
