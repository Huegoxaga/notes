# Discrete Mathematics

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

## Modular Arithmetic

- Modular arithmetic is a system in which all numbers up to some positive integer `n` are used.

### Division Algorithm

- When an integer*(a)* is divided by a positive integer*(b)* we get a quotient*(q)* and a remainder*(r)*.
  - For example, `a = 365,840 and b = 125,460 a = bq + r`

### Modular Systems

- The integers (a) and (b) are **congruent modulo** `m` (where m is a natural number greater than 1) if and only if the difference `a – b`  is divisible by `m`. hence `a` and `b` both have the same remainder when divided by `m`.
- ![$a \equiv b$](https://render.githubusercontent.com/render/math?math=%24a%20%5Cequiv%20b%24) _(mod m)_, From where `a - b = k·m` (for some integer k)
- It also means that there is calculation among the positional number in each mod n system.
- It is like a is circling around a circle of 0 to m-1 and ends up at b.
  so b is like the positional number for a which is counting around the circle.

### Modular Arithmetic

- If ![$a \equiv b$](https://render.githubusercontent.com/render/math?math=%24a%20%5Cequiv%20b%24) _(mod n)_ and ![$c \equiv d$](https://render.githubusercontent.com/render/math?math=%24c%20%5Cequiv%20d%24) _(mod n)_ then:
  - ![$a + c \equiv b + d$](https://render.githubusercontent.com/render/math?math=%24a%20%2B%20c%20%5Cequiv%20b%20%2B%20d%24) _(mod n)_
  - ![$a - c \equiv : b -  d$](https://render.githubusercontent.com/render/math?math=%24a%20-%20c%20%5Cequiv%20%5C%3A%20b%20-%20%20d%24) _(mod n)_
  - ![$a \cdot c \equiv b \cdot d$](https://render.githubusercontent.com/render/math?math=%24a%20%5Ccdot%20c%20%5Cequiv%20b%20%5Ccdot%20d%24) _(mod n)_
  - ![$a^k \equiv b^k$](https://render.githubusercontent.com/render/math?math=%24a%5Ek%20%5Cequiv%20b%5Ek%24) _(mod n)_
- module equation holds by plus and multiply, power operations on both sides. (position number on both sides change together)
  module equation holds by plus and multiply operations with unknowns on both sides.
- As a result, if you want to evaluate `mod p` of an expression just do the arithmetic calculate of both side normally and then simplify by taking the remainder after dividing by p.
- The remainder of a negative number is the negative remain add one full circle.
- ![$a x \equiv b (mod : m)$](https://render.githubusercontent.com/render/math?math=%24a%20x%20%5Cequiv%20b%20%28mod%20%5C%3A%20m%29%24) is called a Congruence equation , unknown `x` is always an integer, `x` will be solved as follow.
  - ![$x \equiv b (mod : m)$](https://render.githubusercontent.com/render/math?math=%24x%20%5Cequiv%20b%20%28mod%20%5C%3A%20m%29%24), where be is an positive integer that is smaller than `m`.
  - The solution for all positive values can also be represented as ![$x \in {b, bm,b+2m, \dotsc }$](https://render.githubusercontent.com/render/math?math=%24x%20%5Cin%20%5C%7Bb%2C%20bm%2Cb%2B2m%2C%20%5Cdotsc%20%5C%7D%24) or ![$x \in \emptyset$](https://render.githubusercontent.com/render/math?math=%24x%20%5Cin%20%5Cemptyset%24) if no solution is found.
- In order to find the positional b of a large number with exponent.
  - find position for the base and the raise the power of the base position number and then find the positional number for the newly generated number.
  - Sometimes when base is not 1 and the exponent is still too big, see if it can be -1.
  - Sometimes the base is divisible on the mod n.

### Application

- The following application has the check digit located at the last digit.
  - Airline Tickets - The check digit is the remainder of the main part divided by 7.
  - Social Insurance Number
    - Luhn algorithm
      - Remove the check digit x
      - Double the even position digits from left and add their digits: (only here: if 12, add 1 and 2. if 14 its 1+4)
      - Add the rest of the digits:
      - multiply by -1
      - The check digit is mod 10
  - UPC – Universal Product Code
    - _check digit =_ ![$-(3a_11+a_10+3a_9+a_8+3a_7+a_6+3a_5+a_4+3a_3+a_2+3a_1); (mod: 10)$](https://render.githubusercontent.com/render/math?math=%24-%283a_11%2Ba_10%2B3a_9%2Ba_8%2B3a_7%2Ba_6%2B3a_5%2Ba_4%2B3a_3%2Ba_2%2B3a_1%29%5C%3B%20%28mod%5C%3A%2010%29%24)
  - ISBN – International Standard Book Number
    - ![a_0 = a_9+2a_8+3a_7+4a_6+5a_5+6a_4+7a_3+8a_2+9a_1 ; (mod : 11)](<https://render.githubusercontent.com/render/math?math=a_0%20%3D%20a_9%2B2a_8%2B3a_7%2B4a_6%2B5a_5%2B6a_4%2B7a_3%2B8a_2%2B9a_1%20%5C%3B%20(mod%20%5C%3A%2011)>)
- Round-Robin Tournament
  - Each team must play against every team once.
  - In even number of teams
    - each team plays in every round
    - the number of rounds is 1 less than the total number of teams.
  - In odd number of teams
    - one team stays with a `bye` (has no match to play)in every round
    - the number of rounds is the same as the total number of teams.
  - In a tournament with N teams
    - Team X will be playing against X in round r, `Y = r-X (mod N or N-1)`
    - When N is odd and Y = X(assumes there is a unknown team x that plays with itself), the team is assigned a bye.
    - When N is even, the schedule is made as there are one less number of teams mod is (N-1) and in case Y = X, the team is assigned to play with Team N.
      - round 0 is round N.
      - careful about TeamN in even Team situation.

## Boolean Algebra

- A logical statement can have two values, True (1) and False (0)
- Boolean Constant is a value that does not change during an operation. It can have values of 1 or 0 only;
- Boolean Variable is a value that can change during an operation (but only from 1 to 0 or from 0 to 1). They are represented by uppercase letters from `A` to `Z`;
- Logical statements can be assigned a value of a constant or a variable and can be combined with Boolean operations. The basic Boolean operations are:
  - Negation (NOT) - `-A`
    - not `A`
  - Conjunction (AND) - `A X B`
    - Both `A` and `B`
  - Disjunction (OR) - `A + B`
    - Either `A` or `B` or both.
  - Exclusive Disjunction (XOR) - `A ⊕ B`
    - Either `A` or `B` but not both.
- Using Block Diagram Symbol
  - NOT Gate ![NOT Gate](img/d-not-gate.png)
  - AND Gate ![AND Gate](img/d-and-gate.png)
  - OR Gate ![OR Gate](img/d-or-gate.png)
  - XOR Gate ![XOR Gate](img/d-xor-gate.png)
  - To represent a expression ![Block Diagram Expression](img/d-block-expression.png)
- If an expression is made up of several smaller expressions (terms) OR-ed together, the expression is in Sum Form. (`A + B + C`)
- If an expression is made up of several smaller expressions AND-ed together, the expression is in product form. (`A X B X C`)
- If every term of the sum form is a product of the variables, the expression is in Sum-of-Product (SOP) form. `A X B + B X C`
- If every term of the product form is a sum of variables, the expression is in Product-of-Sum (POS) form. (`(A + B) X (B + C)`)

#### Manipulate Boolean Expression

- Here are the laws related to boolean expressions. Each law has an `AND` form and an `OR` form
  - Identity law: `1A = A`, `0 + A = A`
  - Null law: `0A = 0`, `1 + A = 1`
  - Idempotent law: `AA = A`, `A + A = A`
  - Inverse law: ![inverse-1](https://render.githubusercontent.com/render/math?math=%24A+%5Coverline%7BA%7D+%3D+0%24), ![$A + \overline{A} = 1$](https://render.githubusercontent.com/render/math?math=%24A+%2B+%5Coverline%7BA%7D+%3D+1%24)
  - Commutative law: `AB = BA`, `A + B = B + A`
  - Associative law: `(AB)C = A(BC)`, `(A + B) + C = A + (B + C)`
  - Distributive law: `A + BC = (A + B)(A + C)`, `A(B + C) = AB + AC`
  - Absorption law: `A(A + B) = A`, `A + AB = A`
  - De Morgan's law: ![$\overline{AB} = \overline{A} + \overline{B} $](https://render.githubusercontent.com/render/math?math=%24%5Coverline%7BAB%7D+%3D+%5Coverline%7BA%7D+%2B+%5Coverline%7BB%7D+%24), ![$\overline{A+B} = \overline{A} \overline{B} $](https://render.githubusercontent.com/render/math?math=%24%5Coverline%7BA%2BB%7D+%3D+%5Coverline%7BA%7D+%5Coverline%7BB%7D+%24)
  - ![$A (\overline{A} + B) = AB$](https://render.githubusercontent.com/render/math?math=%24A+%28%5Coverline%7BA%7D+%2B+B%29+%3D+AB%24), ![$A + \overline{A}B = A+B$](https://render.githubusercontent.com/render/math?math=%24A+%2B+%5Coverline%7BA%7DB+%3D+A%2BB%24)

#### Truth Tables

- It is used to list all the possible combination of the boolean variable in an expression.
- ![Truth Tables](img/d-truth-table.png)
  - Parts of the expression and be written in additional columns on the right.
  - The parts of an expression can be combined using correspoding operation.
- An unknown expression can be solved using truth table.
  - ![Solve Expression](img/d-solve-expression.png)

#### Karnaugh Maps

- It can be used to represent the result of a unknown expresssion according all the possible combination of its variables.
- For two variables:
  - ![KARNAUGH MAPS-2](img/d-karnaugh-2.png)
  - ![KARNAUGH MAPS-3](img/d-karnaugh-3.png)
  - ![KARNAUGH MAPS-4](img/d-karnaugh-4.png)
- From a given Boolean expression, the cells that correspond to terms in the expression will have 1s and the other cells will stay empty. In order to group 1s (to loop 1s) we have the following rules:
  - we can only make loops of one, two, four, eight, … (power of 2 only) 1s;
  - we can loop 1s that are adjacent, above and below, and side by side, but not diagonally;
  - we can include 1s that are already looped in a new loop to form a bigger group;
    - the loops are only rectangular, not T- or L-shaped;
  - we make the biggest loops possible and
  - we make the smallest amount of loops.
- For all previous Boolean expressions, each term contained all variables present. If an expression has terms that are missing a variable (or more variables) we can expand that term by adding all possible combinations of the missing variable (variables).
