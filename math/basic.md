# Basic Math

## Arithmetic

## Roman Numeral System

- Roman Numeral System uses the following character to represent numbers:
  - `I`(1)
  - `X`(10)
  - `C`(100)
  - `M`(1000)
  - `V`(5)
  - `L`(50)
  - `D`(500)
- The following rules are satisfied when writing and reading roman numerals:
  - Two or three same digits (from I, X, C, M) in a row represent the sum of their individual value. For example: `II = 2; CCC=300; MMM=3000;`
  - Two digits where the smaller one is after the bigger represent their sum. For example: `VI = 6; XI = 11; LV=55;`
  - Two digits where the smaller one is in front of the bigger represent their difference. For example: `IV = 4; IX = 9; XL=40;`
  - There can only be put one smaller digit (from `I`, `X`, `C`) in front of a bigger; the smaller letter can be one fifth (1/5) or one tenth (1/10) of the larger one; For example, 99 cannot be `IC` as `I` is one hundredth part of `C`. Instead, 99 can be written as `XCIX` (90 + 9).
  - There can be one, two or three of the same digits that are smaller written after a bigger digit, in which case their value will be added together and added again to the bigger digit. For example: there can only be `CM=900`, but there can be `MCCC=1300`.
  - There cannot be more than one digit written together from the second row of digits above (`V`, `L`, `D`).

## Significant Digits

- `~` is used to on a `0` to represent significant digits.
- Accuracy is represented by the number of significant digits.
- Precision is represented by the place value of the right-most digit.
- Calculation involved in significant digits
  - and - use precision
  - and / use sig dig
  - when together, retain the sig dig and use precision or sig dig according to the last operation.
- ENGINEERING FORMAT
  - use only exponent that can be divided by 3. Ex. E+3 E+9
- Number prefix

| Prefix | Abrre | Value | Name     |
| ------ | ----- | ----- | -------- |
| tera   | T     | 10^12 | trillion |
| giga   | G     | 10^9  | billion  |
| mega   | M     | 10^6  | million  |
| kilo   | k     | 10^3  | thousand |
| hecto  | h     | 10^2  | hundred  |
| deca   | da    | 10^1  | ten      |
|        | 10^0  | one   |          |

## Number Theory

- Number theory is the branch of mathematics concerned with the integers.
- A **prime number** is an integer greater than 1 whose only positive divisors are 1 and itself.
- A **composite number** is an integer greater than 1 that is not a prime. It can be written as a product of integers greater than 1.
- The **factors** of a composite number is all the integer that can can divide the number into an integer.
- Test for Primality - Test if a number if a prime
  - It can be done by checking if the number is divisible by any prime number in the range from 2 to its square root.
- Prime factorization - Prime factorization of a number is to find a product of primes with the same value
  - Ex, ![$28050 = 2\times3\times5^2\times11\times17$](https://render.githubusercontent.com/render/math?math=%2428050%20%3D%202%5Ctimes3%5Ctimes5%5E2%5Ctimes11%5Ctimes17%24) (this is the format for prime factorization result)

> ##### The Fundamental Theorem of Arithmetic
>
> Every integer greater than 1 is either prime or can be expressed as a product of primes in a unique order in which the factors occur.

### Divisibility Rules

- Divisibility rule for 2: All even numbers are divisible by 2;
- Divisibility rule for 3: A number, n, is divisible by 3 if and only if the sum of its digits is divisible by 3;
- Divisibility rule for 4: A number, n, is divisible by 4 if and only if the last two digits form a number divisible by 4;
- Divisibility rule for 5: A number, n, is divisible by 5 if and only if the number finishes at 0 or 5;
- Divisibility rule for 6: If a number, n, is divisible by 2 and 3 at the same time, it is divisible by 6;
- Divisibility rule for 7: For this rule we need to repeat the following step:
  the last digit doubled subtracted this doubled value from the first part(132 for 1327) of the number. Repeat the step as necessary. If the last number is divisible by 7 than n is divisible by 7.
- Divisibility rule for 8: A number, n, is divisible by 8 if the last three digits form a number divisible by 8.
- Divisibility rule for 9: A number, n, is divisible by 9 if and only if the sum of its digits is divisible by 9;
- Divisibility rule for 10: A number, n, is divisible by 10 if and only if the number finishes at 0;
- Divisibility rule for 11: A number, n, is divisible by 11 if and only if the alternating sum(put - and + in between )(order doesn’t matter) of its digits is divisible by 11; when find the divisibility rule of a large number, try the condition that satisfied all the rules for its biggest factor found above.

### GCF & LCM

- A Greatest Common Factor, GCF, of two (or more) numbers is the biggest number that we can divide with (is a factor of) both numbers.
  - It can be express as ![$A \cap B$](https://render.githubusercontent.com/render/math?math=%24A%20%5Ccap%20B%24), when A and B are the set of factors of the two numbers.
- A Least Common Multiple, LCM, of two (or more) numbers is the smallest number that both numbers will divide into.
  - It can be express as ![$A \cup B$](https://render.githubusercontent.com/render/math?math=%24A%20%5Ccup%20B%24), when A and B are the set of factors of the two numbers.
- Euclidian Algorithm
  - It can be used to find the GCF of two large numbers.
  - For Example, find the GCF of 125,460 and 365,840.
    1. ![$365840 = 2 \times 125460 + 114920$](https://render.githubusercontent.com/render/math?math=%24365840%20%3D%202%20%5Ctimes%20125460%20%2B%20114920%24)
    2. ![$125460 = 1 \times 114920 + 10540$](https://render.githubusercontent.com/render/math?math=%24125460%20%3D%201%20%5Ctimes%20114920%20%2B%2010540%24)
    3. ![$114920 = 10 \times 10540 + 9520$](https://render.githubusercontent.com/render/math?math=%24114920%20%3D%2010%20%5Ctimes%2010540%20%2B%209520%24)
    4. ![$10540 = 1 \times 9520 + 1020 $](https://render.githubusercontent.com/render/math?math=%2410540%20%3D%201%20%5Ctimes%209520%20%2B%201020%20%24)
    5. ![$9520 = 9 \times 1020 + 340 $](https://render.githubusercontent.com/render/math?math=%249520%20%3D%209%20%5Ctimes%201020%20%2B%20340%20%24)
    6. ![$1020 = 3 \times 340 + 0$](https://render.githubusercontent.com/render/math?math=%241020%20%3D%203%20%5Ctimes%20340%20%2B%200%24)

### Number Systems

- It is used to represent numbers. It can be one of the follows:
  - Decimal - A decimal number system is consisted of `1` and `9`.
  - Binary - A binary number system is consisted of `1` and `0`.
  - Octor - A octor number system is consisted of `0` - `7`.
  - Hex - A hux number is system consisted of `1` to `9`, then `A` to `F`.
- Convert from other number system to decimal number system
  - for left side before ‘.’ sign
    - from left to right digit one by one, add the number and times the number that can be represent in one digit in the corresponding system(binary 2, oct 8 hex 16) , operation ends with adding the last digit.
  - for right side before ‘.’ sign
    - from right to left digit one by one, add the number and divide the number that can be represent in one digit in the corresponding system(binary 2, oct 8 hex 16) , operation ends with dividing the last digit.
- Convert from decimal number system to other number system
  - for left side before ‘.’ sign
    - divide the number by 2/8/16 record the reminder. keep the integer then keep dividing until reach 0. Use the reminders to compose the new number from right to left.
  - for right side before ‘.’ sign
    - times the decimal with 2/8/16, record all the integer, and keep only the decimal then keep multiplying. the new number are composed by the recorded integer from right to left.
- Conversion between octal and hexadecimal numbers
  - Use binary number as a medium.
    - octal can be changed to a group of 3 binary.
    - Hexadecimal can be changed to a group of 4 binary.
- Representing negative binary numbers
  - SIGN MAGNITUDE NUMBER SYSTEM
    - Use the first digit represent sign, for `8`-bit register, `10000001` is `-1`, `00000001` is `1`
  - ONE’s COMPLEMENT NUMBER SYSTEM
    - change `0` to `1` and `1` to `0` for the number. still, starts with `0` is positive number. `1` is negative.
    - for conversion of negative number simply convert them back to normal form.
    - no change needed to convert positive number
  - TWO’s COMPLEMENT NUMBER SYSTEM
    - based on one’s complement add an `1` in the end.
    - to convert it to decimal, add a minus sign on the left most digit and use the standard method to add rest of the digit into a decimal number.
    - to expanding register size filling the left register positions with the original most left value.
- shortcut for binary subtraction.
  - convert the subtrahend to two’s complement and add with minuend, if the result has more digit than original register size trucate it and it is called overflow.

## Algebra

### Vector

## Geometry
