```C
// arithmetic_operator.cㄴ
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {
	int x, y, result;

	printf("Input two decimals: ");
	scanf("%d %d", &x, &y); // Input: 10 3

	result = x + y;
	printf("%d + %d = %d\n", x, y, result); // Output: 10 + 3 = 13

	result = x - y;
	printf("%d - %d = %d\n", x, y, result); // Output: 10 - 3 = 7

	result = x * y;
	printf("%d * %d = %d\n", x, y, result); // Output: 10 * 3 = 30

	result = x / y;
	printf("%d / %d = %d\n", x, y, result); // Output: 10 / 3 = 3

	result = x % y;
	printf("%d %% %d = %d\n", x, y, result); // Output: 10 % 3 = 1

	return 0;
}
```


```C
// conditional_operator.c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {
	int x, y;

	printf("Input num1: ");
	scanf("%d", &x); // Input: 20

	printf("Input num2: ");
	scanf("%d", &y); // Input: 25

	// conditional operator
	// ()안의 conditional statement의 return이 1이라면 ? 뒤의 값을,
	// ()안의 conditional statement의 return이 0이라면 : 뒤의 값을 리턴함.
	int max = (x > y) ? x : y; // Return: y
	printf("Larger num is %d \n", max); // Output: Larger num is 25

	return 0;
}
```


```C
// increment_operator.c
// decrement도 물론 가능함
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {
	int x, y;

	x = 1;
	y = ++x; // ++x를 먼저 수행하고, y=x 수행
	printf("x=%d  y=%d \n", x, y); // Output: x=2  y=2

	x = 1;
	y = x++; // y=x를 먼저 수행하고, x++ 수행
	printf("x=%d  y=%d \n", x, y); // Output: x=2 y=1

	return 0;
}
```


```C
// relational operator
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {
	int x, y;

	printf("Input two decimals: ");
	scanf("%d %d", &x, &y); // Input: 10 4

	// Output에서 "%d == %d is:"는 생략함
	printf("%d == %d is: %d \n", x, y, x == y); // Output: 0
	printf("%d != %d is: %d \n", x, y, x != y); // Output: 1
	printf("%d > %d is: %d \n", x, y, x > y);   // Output: 1
	printf("%d < %d is: %d \n", x, y, x < y);   // Output: 0
	printf("%d >= %d is: %d \n", x, y, x >= y); // Output: 1
	printf("%d <= %d is: %d \n", x, y, x <= y); // Output: 0

	return 0;
}
```


```C
// bitwise_operator.c
#include <stdio.h>

int main(void) {
	int x = 9;   // 0b1001  
	int y = 10;  // 0b1010

	// bitwise AND by Ampersand(&)
	// Output: 00000009 & 0000000A = 00000008
	printf("%08X & %08X = %08X\n", x, y, x & y); // same as 0b1000


	// bitwise OR by Pipe(|)
	// Output: 00000009 | 0000000A = 0000000B
	printf("%08X | %08X = %08X\n", x, y, x | y); // same as 0b1011

	// bitwise XOR by Caret(^)
	// Output: 00000009 ^ 0000000A = 00000003
	printf("%08X ^ %08X = %08X\n", x, y, x ^ y); // same as 0b0011

	// bitwise NOT by Tilde(~)
	// Output: ~ 00000009 = FFFFFFF6
    	// cf. bitwise NOT은 모든 bit를 반전시킨다,
	// 따라서 2진수에서는 0 <-> 1로 서로 반전되고,
	// 16진수에서는 0 <-> F로 서로 반전된다.
	printf("~ %08b = %08b\n", x, ~x);			 // same as 0b0110

	return 0;
}
```


```C
// shift_operator.c
#include <stdio.h>

int main(void) {
    int x = 9; // 0b1001  

    // Left Shifting is Multiply 2
    // Output: 9 << 1 = 18
    printf("%d << 1 = %d\n", x, x << 1); // 0b10010 = 16+2 = 18

    // Right Shifting is Divide 2
    // Output: 9 >> 1 = 4 // .5는 버림
    printf("%d >> 1 = %d\n", x, x >> 1); // 0b00100 = 4

    return 0;
}
```
![Bitwise Operator](/C_Overview/5_Images/Image1.JPG)  
*Bit Shift*
