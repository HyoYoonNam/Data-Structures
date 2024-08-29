# Section1. 순차 자료구조와 선형 리스트의 이해
## 1. 1. Linear Data Structure; 순차 자료구조
**Linear Data Structure**는 data를 memory에 빈 자리 없이 sequential하게 저장하는 구현 방식이다. 따라서 이 경우에는 logical한 순서와 physical한 순서가 항상 일치해야 한다. C에서는 array를 통해 구현할 수 있다.  


## 1. 2. Linear List; 선형 리스트
**Linear List**는 구현 방식에 따라 두 가지로 나눌 수 있다. 엄밀히 말하면 두 가지 모두 Linear List이지만 전자를 Linear List, 후자를 Linked List라고 부르는 것이 관례이다.  
* Linear Sequential List => Linear List
* Linear Linked List => Linked List

Linear Data Structure의 경우 element가 시작 위치부터 빈 자리 없이 sequential하게 저장되기 때문에, 시작 위치와 element의 크기만 알면 각 element의 위치를 쉽게 알 수 있다.  
ex. 시작 위치가 $\alpha$인 char array의 경우 각 element가 1byte이기 때문에 5번 째 element의 위치는 $\alpha + 4$이다.


## 1. 3. Linear List를 array로 구현하기
### 1 dimensional array
```c
#include <stdio.h>

int main(void) {
    // 1 dimensional array
    int sale[4] = { 157, 209, 251, 312 };
    int i;

    for (i = 0; i < 4; i++) {
        printf("address: %p sale[%d] = %d \n", &sale[i], i, sale[i]);
    }

    return 0;
}
```

```text
Output:
address: 00AFF980 sale[0] = 157
address: 00AFF984 sale[1] = 209
address: 00AFF988 sale[2] = 251
address: 00AFF98C sale[3] = 312
```
여기서 Linear Data Structure의 특징을 확인할 수 있다.  
1. 어떤 element의 index가 다른 element보다 크다면, address 또한 크다.  
   sale[1]의 index는 1, sale[0]의 index는 0이고 address는 각각 ...84, ...80이다.
2. (int의 경우) 다음 index의 element의 address는 현재 index의 element의 address보다 4byte 만큼 크다.

### 2 dimensional array
logical하게 보면 index를 두 개 사용하여 2 dimensional로 표현할 수 있지만, memory(physical)에는 결국 1 dimensional로 저장된다.  
이때 2-dim을 1-dim으로 convert하는 방법에는 **row major order**과 **column major order**가 있다. C는 전자를 사용한다.  

```c
#include <stdio.h>

int main(void) {
    // 2 dimensional array
    int sale[2][4] = { { 63, 84, 140, 130 },
                       {157, 209, 251, 312 } };
    int i;
    int* ptr = &sale;

    for (i = 0; i < 8; i++) {
        printf("address: %p sale %d = %d \n", ptr+i, i, *(ptr+i));
    }

    return 0;
}
```

```text
Output:
address: 003DFD10 sale 0 = 63
address: 003DFD14 sale 1 = 84
address: 003DFD18 sale 2 = 140
address: 003DFD1C sale 3 = 130
address: 003DFD20 sale 4 = 157
address: 003DFD24 sale 5 = 209
address: 003DFD28 sale 6 = 251
address: 003DFD2C sale 7 = 312
```

### 3 dimensional array
```c
#include <stdio.h>

int main(void) {
    int sale[2][2][4] = { { { 63, 84, 140, 130 },
                            { 157, 209, 251, 312 } },
                          { { 59, 80, 130, 135 },
                            { 149, 187, 239, 310 } } };
    int i;
    int* ptr = &sale;

    for (i = 0; i < (sizeof(sale) / sizeof(int)); i++) {
        printf("address: %p sale %2d = %3d \n", ptr, i, *ptr);
        ptr++;
    }
}
```


# Section2. Insert, Delete
Linear Data Structure는 Insert나 Delete 연산 이후에도 Linearity가 유지되도록 해야 한다.  



