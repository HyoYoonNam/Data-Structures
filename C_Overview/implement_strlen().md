# `strlen()` 직접 구현하기
```C
#include <stdio.h>
#include <string.h>

int compute_len(char str[]);

int main(void) {
    char str[] = "abcdefgh"; // double quotation으로 감싼 경우에는 \0 자동으로 추가.
    printf("%d \n", sizeof(str)); // Output: 9

    int len = strlen(str);
    printf("문자열 %s의 길이: %d \n", str, len);

    int len2 = compute_len(str);
    printf("문자열 %s의 길이: %d \n", str, len2);

    return 0;
}

/* strlen을 직접 구현해보면 다음과 같음.*/
int compute_len(char str[]) {
    int len = 0;

    while (str[len] != '\0') {
        len++;
    }

    return len;
}
```
