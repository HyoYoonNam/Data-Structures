# strcat() 직접 구현하기
직접 구현하던 도중에 감명깊은 에러를 마주해서 기록함.
```C
#include <stdio.h>
#include <string.h>

void concatenate_string(char s1[], char s2[]);

int main(void) {
    char s[11] = "Hello";
    //printf("%d \n", sizeof(s)); // Output: 11 여기서는 parameter로 넘긴 게 아니라서. 
    //strcat(s, "World");
    concatenate_string(s, "World");
    printf("%s \n", s);

    return 0;
}

// parameter로 넘길 때는 s를 pointer로 넘기기 때문에 size가 4byte가 된다.
void concatenate_string(char s1[], char s2[]) {
    // s1의 끝 지점(=s2를 붙일 시작점) 찾기
    //printf("%d \n", sizeof(s2)); // Output: 4 (pointer의 크기는 data type관계없이 4)
    int i;
    //printf("%d \n", strlen(s1)); // Output: 5 (strlen()을 사용하면 됨)
    for (i = 0; i < sizeof(s1); i++) // pointer로 넘어왔기 때문에 sizeof()를 사용하면 제대로 작동x. 
        if (s1[i] == '\0') break;

    // s1에 s2를 한 글자씩 붙이기
    int j;
    for (j = 0; j < sizeof(s2); j++)
        s1[i++] = s2[j];

    return;

// 결론: 제대로 작동시킬 거면 sizeof()를 둘 strlen()으로 바꿔주면 된다.
// 안 바꿔 둔 이유는 감명깊은 오류라서.
// 아니면 다음과 같이 해도 된다.
    // for (i = 0; s1[i] != '\0'; i++);
    // for (j = 0; s2[j] != '\0'; j++)
    //     s1[i++] = s2[j];
}
```
