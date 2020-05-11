# Mathematics

# Arithmetic

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
  the last digit doubled subtracted this doubled value from the first part(132for1327) of the number. Repeat the step as necessary. If the last number is divisible by 7 than n is divisible by 7.
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
- ![$a x \equiv b (mod : m)$](<https://render.githubusercontent.com/render/math?math=%24a%20x%20%5Cequiv%20b%20(mod%20%5C%3A%20m)%24>) is called a Congruence equation , unknown `x` is always an integer, `x` will be solved as follow.
  - ![$x \equiv b (mod : m)$](<https://render.githubusercontent.com/render/math?math=%24x%20%5Cequiv%20b%20(mod%20%5C%3A%20m)%24>), where be is an positive integer that is smaller than `m`.
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
    - _check digit =_ ![$-(3a_11+a_10+3a_9+a_8+3a_7+a_6+3a_5+a_4+3a_3+a_2+3a_1); (mod: 10)$](<https://render.githubusercontent.com/render/math?math=%24-(3a_11%2Ba_10%2B3a_9%2Ba_8%2B3a_7%2Ba_6%2B3a_5%2Ba_4%2B3a_3%2Ba_2%2B3a_1)%5C%3B%20(mod%5C%3A%2010)%24>)
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

# Basic Algebra

# Calculus

# Linear Algebra

# Probability

# Statistics
