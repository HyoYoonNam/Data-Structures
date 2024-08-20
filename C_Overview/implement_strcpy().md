# `strcpy()` 직접 구현하기
array는 기본적으로 pointer이기 때문에 function에 전달하고 무언가를 수행할 때 local variable 문제가 발생하지 않는다.  

```C
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>

void copy_string(char dst[], char src[]);

int main(void) {
    char src[] = "Hello"; // source
    char dst[6]; // destination for strcpy()
    char dst2[6]; // destination2 for copy_string()

    strcpy(dst, src);
    printf("복사된 문자열: %s by strcpy() \n", dst);

    copy_string(dst2, src);
    printf("복사된 문자열: %s by copy_string() \n", dst2);

    return 0;
}

void copy_string(char dst[], char src[]) { // array is pointer. 기본적으로 복사해서 전달함 즉 다른 개체.
    // size 확인
    if (sizeof(dst) < sizeof(src)) {
        printf("Error: destination의 size가 source보다 작아서 copy할 수 없습니다. \n");
        return -1; // C에는 Exception Handlling 내장 메커니즘이 없음(C++에는 존재).
                   // 따라서 raise 등이 불가하고, return -1로 에러임을 관례적으로 알릴 수 있음.
    }

    int i = 0;
    do {
        dst[i] = src[i]; // 1. 일단 대입(복사)하고
    } while (src[i++] != '\0'); // 2. i번 째 값이 \0인지 확인하고, i + 1

    return;
}

```
