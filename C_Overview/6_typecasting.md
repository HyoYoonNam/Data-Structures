```C
// typecasting.c
#include <stdio.h>
int main(void)
{
	int i;
	double f;

	// 일단 int에 대해서 5/4를 하고 float에 저장하기 때문에 1을 double로 변환
	f = 5 / 4; 
	// Output: (5 / 4) = 1.000000
	printf("(5 / 4) = %f\n", f);

	// double 5랑 int 4를 연산
	f = (double)5 / 4; // double로 explicit casting되는 것은 5만 적용됨
	                   // 4는 (double)5와 연산되면서 implicit typecasting
	// Output: (double)5 / 4 = 1.250000
	printf("(double)5 / 4 = %f\n", f);

	// 3.1을 int에 집어 넣으니 3이 됨
	i = 1.3 + 1.8;
	printf("1.3 + 1.8 = %d\n", i);
	// Output: 1.3 + 1.8 = 3

	// 1.3과 1.8을 각각 int로 casting하고 더하고 int에 넣음
	i = (int)1.3 + (int)1.8;
	printf("(int)1.3 + (int)1.8 = %d\n", i);
	// Output: (int)1.3 + (int)1.8 = 2

	return 0;
}
```
