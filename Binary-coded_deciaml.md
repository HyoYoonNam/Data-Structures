# Table of contents
* [Binary-coded decimal](#binary-coded-decimal)
  - [Zoned-decimal format](#zoned-decimal-format)
  - [Packed-decimal format](#packed-decimal-format)


# Binary-coded decimal
**binary-coded decimal (BCD)** is a class of binary encodings of decimal numbers where each digit is represented by a fixed number of bits, usually four or eight.  
> Both **Zoned Decimal** and **Packed Decimal** formats are types of BCD because they represent decimal digits in a binary form.  
  당연하게도 이 둘 외에도 더 있다.


## Zoned-decimal format
**Zoned-decimal format** means that each byte of storage can contain one digit or one character.  
In the zoned-decimal format, each byte of storage is divided into two portions: a 4-bit zone portion and a 4-bit digit portion.  

*Table 1. Zoned-Decimal Format*
<table>
    <thead>
        <tr>
            <th colspan="4">Zone Portion (4-bit)</th>
            <th colspan="4">Digit Portion (4-bit)</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>$z_1$</td>
            <td>$z_2$</td>
            <td>$z_3$</td>
            <td>$z_4$</td>
            <td>$d_1$</td>
            <td>$d_2$</td>
            <td>$d_3$</td>
            <td>$d_4$</td>
        </tr>
        <tr>
            <td>0 or 1</td>
            <td>0 or 1</td>
            <td>0 or 1</td>
            <td>0 or 1</td>
            <td>0 or 1</td>
            <td>0 or 1</td>
            <td>0 or 1</td>
            <td>0 or 1</td>
        </tr>
    </tbody>
</table>

* Zoned-decimal format은 기본적으로 8bit(1byte)를 한 단위로 하여 `Decimal`을 `Binary`로 표현할 수 있다.
* Zone Portion은 기본적으로 모두 `1`로 채운다. 즉 `0b1111`이므로, `0xF`로 나타낼 수도 있음.
* Digit Portion의 $d_1$ ~ $d_4$는 표현하고 싶은 Decimal을 Binary로 변환하면 된다.
* Ex. $`9_{(10)}`$ can be represented as $`1100\ 0101_{(2)}`$ or $`C9_{(16)}`$ in zoned-decimal format.

**Question 1. 두 자리의 Decimal을 표현하려면**  
* $`12_{(10)}`$을 zoned-decimal format으로 표현하는 방법은 다음과 같다.
* (이렇게 하면 안 된다) $`1111\ 1100_{(2)}`$ or $`FC_{(16)}`$
* (이렇게 해야 된다) $`1111\ 0001\ \ \ 1100\ 0010_{(2)}`$ or $`F1\ C2_{(16)}`$  
  Decimal의 각 자리수마다 Zoned-decimal format을 1:1로 대응시킨다고 이해하면 된다.

**Question2. Zoned Portion이 `1111`일 때와 `1100`일 때의 차이**  
* 위에서 "Zone Portion은 기본적으로 모두 `1`로 채운다."라고 했었는데 이에 대해서 더 자세히 다뤄보자.
* `1100(C)`은 **Positive Sign**을 의미한다. 추가적으로 `1101(D)`은 **Negative Sign**을 의미한다.
  그리고 Sign은 **한 번만(!!!)** 구분해주면 된다.
  - Ex. $`+12_{(10)}`$를 Zoned-decimal format으로 표현하고 싶다면 $`C1\ C2_{(16)}`$이라고 두 번 표현할 필요없이, $`F1\ C2_{(16)}`$라고 한 번만 표현해주면 된다.
  - 이때 **Sign을 표현해주는 위치**는 마지막 자리에서만(!!!) 해주면 된다.  
    앞선 예시의 $`F1\ C2_{(16)}`$에서 `1`은 첫 번째 자리, `2`는 마지막 자리이다.
  - 그리고 마지막 자리가 아닌 나머지 자리는 모두 $`1111_{(2)}`$ 즉, $`F_{(16)}`$으로 채워주면 된다.
* Ex1. $`+512_{(10)}`$ can be represented as $`F5\ F1\ C2_{(16)}`$ in zoned-decimal format(C for Positive sign).  
  Ex2. $`-512_{(10)}`$ can be represented as $`F5\ F1\ D2_{(16)}`$ in zoned-decimal format(D for Negative sign).


## Packed-decimal format

