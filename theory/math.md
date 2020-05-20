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

## Limit

#### Definition

- Intuitive Definitions
  - Definition of a Limit
    - Suppose _`f(x)`_ is defined when `x` is near the number `a`. (This means that f is defined on some open interval that contains a, except possibly at a itself.) Then we write ![$\lim_{x \to a}f(x)=L$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x)%3DL%24>) and say "the limit of f sxd, as x approaches a, equals L" if we can make the values of _`f(x)`_ arbitrarily close to L (as close to L as we like) by restricting x to be sufficiently close to a (on either side of a) but not equal to a.
  - Definition of One-Sided Limits
    - ![$\lim_{x \to a^-}f(x)=L$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E-%7Df(x)%3DL%24>) and say the left-hand limit of _`f(x)`_ as x approaches a [or the limit of f sxd as x approaches `a` from the left] is equal to `L` if we can make the values of _`f(x)`_ arbitrarily close to `L` by taking `x` to be sufficiently close to a with `x` less than `a`.
    - ![$\lim_{x \to a^+}f(x)=L$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E%2B%7Df(x)%3DL%24>) if we require that x be greater than a, we get "the right-hand limit of _`f(x)`_ as `x` approaches `a` is equal to `L`".
  - Definition of an Infinite Limit
    - Let `f` be a function defined on both sides of `a`, except possibly at `a` itself. Then ![$\lim_{x \to a}f(x)= \infty$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x)%3D%20%5Cinfty%24>) means that the values of _`f(x)`_ can be made arbitrarily large (as large as we please) by taking `x` sufficiently close to `a`, but not equal to `a`.
    - Let `f` be a function defined on both sides of `a`, except possibly at `a` itself. Then ![$\lim_{x \to a}f(x)= - \infty$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x)%3D%20-%20%5Cinfty%24>) means that the values of _`f(x)`_ can be made arbitrarily large negative by taking `x` sufficiently close to `a`, but not equal to `a`.
  - Definition of a Limit at Infinity
    - Let _f_ be a function defined on some interval ![$(a, \infty)$](<https://render.githubusercontent.com/render/math?math=%24(a%2C%20%5Cinfty)%24>). Then ![$\lim_{x \to \infty}f(x)= L$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20%5Cinfty%7Df(x)%3D%20L%24>) means that the values of _f(x)_ can be made arbitrarily close to _L_ by requiring _x_ to be sufficiently large.
    - Let _f_ be a function defined on some interval ![$(a, -\infty)$](<https://render.githubusercontent.com/render/math?math=%24(a%2C%20-%5Cinfty)%24>). Then ![$\lim_{x \to - \infty}f(x)= L$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20-%20%5Cinfty%7Df(x)%3D%20L%24>) means that the values of _f(x)_ can be made arbitrarily close to _L_ by requiring _x_ to be sufficiently large negative.
  - Definition of an Infinite Limit at Infinity
    - Let _f_ be a function defined on some interval ![$(a, \infty)$](<https://render.githubusercontent.com/render/math?math=%24(a%2C%20%5Cinfty)%24>). Then ![$\lim_{x \to \infty}f(x)= \infty$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20%5Cinfty%7Df(x)%3D%20%5Cinfty%24>) means that for every positive number _M_ there is a corresponding positive number _N_ such that if ![$x > N$](https://render.githubusercontent.com/render/math?math=%24x%20%3E%20N%24) then ![$f(x) > M$](<https://render.githubusercontent.com/render/math?math=%24f(x)%20%3E%20M%24>)
- Precise Definitions
  - Definition of a Limit
    - Let _`f`_ be a function defined on some open interval that contains the number _`a`_, except possibly at _`a`_ itself. Then we say that the limit of _`f(x)`_ as _`x`_ approaches _`a`_ is _`L`_, and we write ![$\lim_{x \to a}f(x) = L$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x)%20%3D%20L%24>) if for every number ![$\epsilon > 0$](https://render.githubusercontent.com/render/math?math=%24%5Cepsilon%20%3E%200%24) there is a number ![$\delta > 0$](https://render.githubusercontent.com/render/math?math=%24%5Cdelta%20%3E%200%24) such that, if ![$0 < |x-a| < \delta$](https://render.githubusercontent.com/render/math?math=%240%20%3C%20%7Cx-a%7C%20%3C%20%5Cdelta%24) then ![$|f(x) - L| < \epsilon$](<https://render.githubusercontent.com/render/math?math=%24%7Cf(x)%20-%20L%7C%20%3C%20%5Cepsilon%24>)
  - Definition of One-Sided Limits
    - ![$\lim_{x \to a^-}f(x) = L$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E-%7Df(x)%20%3D%20L%24>) if for every number ![$\epsilon > 0$](https://render.githubusercontent.com/render/math?math=%24%5Cepsilon%20%3E%200%24) there is a number ![$\delta > 0$](https://render.githubusercontent.com/render/math?math=%24%5Cdelta%20%3E%200%24) such that, if ![$a - \delta < x < a$](https://render.githubusercontent.com/render/math?math=%24a%20-%20%5Cdelta%20%3C%20x%20%3C%20a%24) then ![$|f(x) - L| < \epsilon$](<https://render.githubusercontent.com/render/math?math=%24%7Cf(x)%20-%20L%7C%20%3C%20%5Cepsilon%24>)
    - ![$\lim_{x \to a^-}f(x) = L$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E-%7Df(x)%20%3D%20L%24>) if for every number ![$\epsilon > 0$](https://render.githubusercontent.com/render/math?math=%24%5Cepsilon%20%3E%200%24) there is a number ![$\delta > 0$](https://render.githubusercontent.com/render/math?math=%24%5Cdelta%20%3E%200%24) such that, if ![$a < x < a + \delta $](https://render.githubusercontent.com/render/math?math=%24a%20%3C%20x%20%3C%20a%20%2B%20%5Cdelta%20%24) then ![$|f(x) - L| < \epsilon$](<https://render.githubusercontent.com/render/math?math=%24%7Cf(x)%20-%20L%7C%20%3C%20%5Cepsilon%24>)
  - Definition of an Infinite Limit
    - Let _`f`_ be a function defined on some open interval that contains the number _`a`_, except possibly at _`a`_ itself. Then ![$\lim_{x \to a}f(x) = \infty$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x)%20%3D%20%5Cinfty%24>) means that for every positive number _M_ there is a positive number ![$\delta$](https://render.githubusercontent.com/render/math?math=%24%5Cdelta%24) such that if ![$0 < |x-a| < \delta$](https://render.githubusercontent.com/render/math?math=%240%20%3C%20%7Cx-a%7C%20%3C%20%5Cdelta%24) then ![$f(x) > M$](<https://render.githubusercontent.com/render/math?math=%24f(x)%20%3E%20M%24>)
    - Let _`f`_ be a function defined on some open interval that contains the number _`a`_, except possibly at _`a`_ itself. Then ![$\lim_{x \to a}f(x) = - \infty$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x)%20%3D%20-%20%5Cinfty%24>) means that for every positive number _M_ there is a negetive number ![$\delta$](https://render.githubusercontent.com/render/math?math=%24%5Cdelta%24) such that if ![$0 < |x-a| < \delta$](https://render.githubusercontent.com/render/math?math=%240%20%3C%20%7Cx-a%7C%20%3C%20%5Cdelta%24) then ![$f(x) < N$](<https://render.githubusercontent.com/render/math?math=%24f(x)%20%3C%20N%24>)
  - Definition of a Limit at Infinity - Let _f_ be a function defined on some interval ![$(a, \infty)$](<https://render.githubusercontent.com/render/math?math=%24(a%2C%20%5Cinfty)%24>). Then ![$\lim_{x \to \infty} f(x) = L$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20%5Cinfty%7D%20f(x)%20%3D%20L%24>) means that for every ![$\epsilon > 0$](https://render.githubusercontent.com/render/math?math=%24%5Cepsilon%20%3E%200%24) there is a corresponding number _N_ such that if ![$x > N$](https://render.githubusercontent.com/render/math?math=%24x%20%3E%20N%24) then ![$| f(x) - L| < \epsilon$](<https://render.githubusercontent.com/render/math?math=%24%7C%20f(x)%20-%20L%7C%20%3C%20%5Cepsilon%24>) - Let _f_ be a function defined on some interval ![$(-\infty , a)$](<https://render.githubusercontent.com/render/math?math=%24(-%5Cinfty%20%2C%20a)%24>). Then ![$\lim_{x \to -\infty} f(x) = L$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20-%5Cinfty%7D%20f(x)%20%3D%20L%24>) means that for every ![$\epsilon > 0$](https://render.githubusercontent.com/render/math?math=%24%5Cepsilon%20%3E%200%24) there is a corresponding number _N_ such that if ![$x < N$](https://render.githubusercontent.com/render/math?math=%24x%20%3C%20N%24) then ![$| f(x) - L| < \epsilon$](<https://render.githubusercontent.com/render/math?math=%24%7C%20f(x)%20-%20L%7C%20%3C%20%5Cepsilon%24>)
- ![$\lim_{x \to a}f(x)=L$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x)%3DL%24>) if and only if ![$\lim_{x \to a^+}f(x)=L$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E%2B%7Df(x)%3DL%24>) and ![$\lim_{x \to a^-}f(x)=L$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E-%7Df(x)%3DL%24>)
- The vertical line `x = a` is called a vertical asymptote of the curve ![$y= f(x)$](<https://render.githubusercontent.com/render/math?math=%24y%3D%20f(x)%24>) if at least one of the following statements is true:
  - ![$\lim_{x \to a}f(x)= \infty$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x)%3D%20%5Cinfty%24>)
  - ![$\lim_{x \to a^-}f(x)= \infty$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E-%7Df(x)%3D%20%5Cinfty%24>)
  - ![$\lim_{x \to a^+}f(x)= \infty$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E%2B%7Df(x)%3D%20%5Cinfty%24>)
  - ![$\lim_{x \to a}f(x)=- \infty$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x)%3D-%20%5Cinfty%24>)
  - ![$\lim_{x \to a^-}f(x)=- \infty$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E-%7Df(x)%3D-%20%5Cinfty%24>)
  - ![$\lim_{x \to a^+}f(x)=- \infty$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E%2B%7Df(x)%3D-%20%5Cinfty%24>)
  - Example: ![$\lim_{x \to 0^+} \ln{x}=- \infty$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%200%5E%2B%7D%20%5Cln%7Bx%7D%3D-%20%5Cinfty%24)
- A function _f_ is continuous at a number a if ![$\lim_{x \to a}f(x) = f(a)$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x)%20%3D%20f(a)%24>)
- A function _f_ is continuous from the right at a number _a_ if ![$\lim_{x \to a^+}f(x) = f(a)$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E%2B%7Df(x)%20%3D%20f(a)%24>)
- A function _f_ is continuous from the left at a number _a_ if ![$\lim_{x \to a^-}f(x) = f(a)$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E-%7Df(x)%20%3D%20f(a)%24>)
- A function _f_ is continuous on an interval if it is continuous at every number in the interval. (If _f_ is defined only on one side of an endpoint of the interval, we understand continuous at the endpoint to mean continuous from the right or continuous from the left.)
- The line _y = L_ is called a horizontal asymptote of the curve _y = f(x)_ if either ![$\lim_{x \to a}f(x)= - \infty$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x)%3D%20-%20%5Cinfty%24>) or ![$(a, -\infty)$](<https://render.githubusercontent.com/render/math?math=%24(a%2C%20-%5Cinfty)%24>). Then ![$\lim_{x \to - \infty}f(x)= L$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20-%20%5Cinfty%7Df(x)%3D%20L%24>)
  - For Example:
    - ![$\lim_{x \to - \infty}\tan^{-1}{x}= - \frac{\pi}{2} $](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20-%20%5Cinfty%7D%5Ctan%5E%7B-1%7D%7Bx%7D%3D%20-%20%5Cfrac%7B%5Cpi%7D%7B2%7D%20%24)
    - ![$\lim_{x \to \infty}\tan^{-1}{x}= \frac{\pi}{2} $](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20%5Cinfty%7D%5Ctan%5E%7B-1%7D%7Bx%7D%3D%20%5Cfrac%7B%5Cpi%7D%7B2%7D%20%24)
    - ![$\lim_{x \to - \infty} e^x = 0$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20-%20%5Cinfty%7D%20e%5Ex%20%3D%200%24)
- Definition of the Number _e_
  - _e_ is the number such that ![$\lim_{h \to 0} \frac{e^h-1}{h} = 1$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bh%20%5Cto%200%7D%20%5Cfrac%7Be%5Eh-1%7D%7Bh%7D%20%3D%201%24)

#### Laws

- Limit Laws, Suppose that `c` is a constant and the limits ![$\lim_{x \to a} f(x)$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20f(x)%24>) and ![$\lim_{x \to a} g(x)$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20g(x)%24>) exist. Then:
  - ![$\lim_{x \to a} [f(x)+g(x)]=\lim_{x \to a} f(x)+\lim_{x \to a} g(x)$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20%5Bf(x)%2Bg(x)%5D%3D%5Clim_%7Bx%20%5Cto%20a%7D%20f(x)%2B%5Clim_%7Bx%20%5Cto%20a%7D%20g(x)%24>) Sum Law
  - ![$\lim_{x \to a} [f(x)-g(x)]=\lim_{x \to a} f(x)-\lim_{x \to a} g(x)$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20%5Bf(x)-g(x)%5D%3D%5Clim_%7Bx%20%5Cto%20a%7D%20f(x)-%5Clim_%7Bx%20%5Cto%20a%7D%20g(x)%24>) Difference Law
  - ![$\lim_{x \to a} [cf(x)]=c \lim_{x \to a} f(x)$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20%5Bcf(x)%5D%3Dc%20%5Clim_%7Bx%20%5Cto%20a%7D%20f(x)%24>) Constant Multiple Law
  - ![$\lim_{x \to a} [f(x)g(x)]=\lim_{x \to a} f(x) \cdot \lim_{x \to a} g(x)$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20%5Bf(x)g(x)%5D%3D%5Clim_%7Bx%20%5Cto%20a%7D%20f(x)%20%5Ccdot%20%5Clim_%7Bx%20%5Cto%20a%7D%20g(x)%24>) Product Law
  - ![$\lim_{x \to a} \frac{f(x)}{g(x)}=\frac{\lim_{x \to a} f(x)}{\lim_{x \to a} g(x)}$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20%5Cfrac%7Bf(x)%7D%7Bg(x)%7D%3D%5Cfrac%7B%5Clim_%7Bx%20%5Cto%20a%7D%20f(x)%7D%7B%5Clim_%7Bx%20%5Cto%20a%7D%20g(x)%7D%24>) if ![$\lim_{x \to a} g(x) \neq 0$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20g(x)%20%5Cneq%200%24>) Quotient Law
  - ![$\lim_{x \to a} [f(x)]^n = \left[\lim_{x \to a} f(x)\right]^n$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20%5Bf(x)%5D%5En%20%3D%20%5Cleft%5B%5Clim_%7Bx%20%5Cto%20a%7D%20f(x)%5Cright%5D%5En%24>) where n is a positive integer, Power Law
  - ![$\lim_{x \to a}c=c $](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Dc%3Dc%20%24)
  - ![$\lim_{x \to a}x=a $](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Dx%3Da%20%24)
  - ![$\lim_{x \to a} x^n=a^n $](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20x%5En%3Da%5En%20%24) where n is a positive integer
  - ![$\lim_{x \to a} \sqrt[n]{x}=\sqrt[n]{a} $](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20%5Csqrt%5Bn%5D%7Bx%7D%3D%5Csqrt%5Bn%5D%7Ba%7D%20%24) where `n` is a positive integer (If `n` is even, we assume that `a > 0`.)
  - ![$\lim_{x \to a} \sqrt[n]{f(x)}=\sqrt[n]{\lim_{x \to a} f(x)} $](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20%5Csqrt%5Bn%5D%7Bf(x)%7D%3D%5Csqrt%5Bn%5D%7B%5Clim_%7Bx%20%5Cto%20a%7D%20f(x)%7D%20%24>) where `n` is a positive integer. If `n` is even, we assume that ![$\lim_{x \to a}f(x) > 0$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x)%20%3E%200%24>). Root Law

#### Properties

- Direct Substitution Property If _`f`_ is a polynomial or a rational function and _`a`_ is in the domain of _`f`_ , then ![$\lim_{x \to a}f(x) = f(a)$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x)%20%3D%20f(a)%24>)
- If ![$f(x)=g(x)$](<https://render.githubusercontent.com/render/math?math=%24f(x)%3Dg(x)%24>) when ![$x \neq a$](https://render.githubusercontent.com/render/math?math=%24x%20%5Cneq%20a%24), then ![$\lim_{x \to a}f(x) = \lim_{x \to a}g(x)$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x)%20%3D%20%5Clim_%7Bx%20%5Cto%20a%7Dg(x)%24>) provided the limits exist.

#### Theorem

- ![$\lim_{x \to a}f(x) = L$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x)%20%3D%20L%24>) if and only if ![$\lim_{x \to a_-}f(x) = L = \lim_{x \to a_+}f(x)$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a_-%7Df(x)%20%3D%20L%20%3D%20%5Clim_%7Bx%20%5Cto%20a_%2B%7Df(x)%24>)
- If ![$f(x) \leqslant g(x)$](<https://render.githubusercontent.com/render/math?math=%24f(x)%20%5Cleqslant%20g(x)%24>) where _`x`_ is near _`a`_ (except possibly at _`a`_) and the limits of _`f`_ and _`g`_ both exist as _`x`_ approaches _`a`_, then ![$\lim_{x \to a}f(x) \leqslant \lim_{x \to a}g(x)$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x)%20%5Cleqslant%20%5Clim_%7Bx%20%5Cto%20a%7Dg(x)%24>)
- The Squeeze Theorem - If ![$f(x) \leqslant g(x) \leqslant h(x)$](<https://render.githubusercontent.com/render/math?math=%24f(x)%20%5Cleqslant%20g(x)%20%5Cleqslant%20h(x)%24>) when _`x`_ is near _`a`_ (except possibly at _`a`_) and ![$\lim_{x \to a}f(x)= \lim_{x \to a}h(x) = L$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x)%3D%20%5Clim_%7Bx%20%5Cto%20a%7Dh(x)%20%3D%20L%24>) then ![$\lim_{x \to a}g(x) = L$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Dg(x)%20%3D%20L%24>)
- If _f_ and _g_ are continuous at _a_ and _c_ is a constant, then the following functions are also continuous at _a_:
  - _f + g_
  - _f - g_
  - _cf_
  - _fg_
  - ![$\frac{f}{g}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bf%7D%7Bg%7D%24) if ![$g(a) \neq 0$](<https://render.githubusercontent.com/render/math?math=%24g(a)%20%5Cneq%200%24>)
- Any polynomial is continuous everywhere; that is, it is continuous on ![$\mathbb{R} = (- \infty, \infty)$](<https://render.githubusercontent.com/render/math?math=%24%5Cmathbb%7BR%7D%20%3D%20(-%20%5Cinfty%2C%20%5Cinfty)%24>).
- Any rational function is continuous wherever it is defined; that is, it is contin- uous on its domain.
- The following types of functions are continuous at every number in their domains:
  - polynomials
  - rational functions
  - root functions
  - trigonometric functions
  - exponential functions
  - inverse trigonometric functions
  - logarithmic functions
- If _f_ is continuous at _b_ and ![$\lim_{x \to a}g(x) = b$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Dg(x)%20%3D%20b%24>), then ![$\lim_{x \to a}f(g(x)) =f(b)$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(g(x))%20%3Df(b)%24>). In other words, ![$\lim_{x \to a}f(g(x)) =f\left(\lim_{x \to a}g(x)\right)$](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(g(x))%20%3Df%5Cleft(%5Clim_%7Bx%20%5Cto%20a%7Dg(x)%5Cright)%24>)
- If _g_ is continuous at _a_ and _f_ is continuous at _g(a)_, then the composite function ![$f \circ g$](https://render.githubusercontent.com/render/math?math=%24f%20%5Ccirc%20g%24) given by ![$(f \circ g)(x) = f(g(x))$](<https://render.githubusercontent.com/render/math?math=%24(f%20%5Ccirc%20g)(x)%20%3D%20f(g(x))%24>) is continuous at _a_.
- The Intermediate Value Theorem - Suppose that _f_ is continuous on the closed interval ![$[a,b]$](https://render.githubusercontent.com/render/math?math=%24%5Ba%2Cb%5D%24) and let _N_ be any number between _f(a)_ and _f(b)_ , where ![$f(a) \neq f(b)$](<https://render.githubusercontent.com/render/math?math=%24f(a)%20%5Cneq%20f(b)%24>). Then there exists _a_ number _c_ in ![$(a,b)$](<https://render.githubusercontent.com/render/math?math=%24(a%2Cb)%24>) such that _f(c) = N_.
- If ![$r > 0$](https://render.githubusercontent.com/render/math?math=%24r%20%3E%200%24) is a rational number, then ![$\lim_{x \to \infty}\frac{1}{x^r}= 0$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20%5Cinfty%7D%5Cfrac%7B1%7D%7Bx%5Er%7D%3D%200%24) If ![$r > 0$](https://render.githubusercontent.com/render/math?math=%24r%20%3E%200%24) is a rational number such that ![$x^r$](https://render.githubusercontent.com/render/math?math=%24x%5Er%24) is defined for all _x_, then ![$\lim_{x \to - \infty}\frac{1}{x^r}= 0$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20-%20%5Cinfty%7D%5Cfrac%7B1%7D%7Bx%5Er%7D%3D%200%24)

#### Related Solving Methods

## Derivatives

#### Definition

- Tangent Line - The tangent line to the curve ![$y = f(x)$](<https://render.githubusercontent.com/render/math?math=%24y%20%3D%20f(x)%24>) at the point ![$P(a, f(a))$](<https://render.githubusercontent.com/render/math?math=%24P(a%2C%20f(a))%24>) is the line through _P_ with slope ![$m = \lim_{x \to a} \frac{f(x)-f(a)}{x-a}$](<https://render.githubusercontent.com/render/math?math=%24m%20%3D%20%5Clim_%7Bx%20%5Cto%20a%7D%20%5Cfrac%7Bf(x)-f(a)%7D%7Bx-a%7D%24>) provided that this limit exists.
  - Optionally, ![$m = \lim_{h \to 0} \frac{f(a+h)-f(a)}{h}$](<https://render.githubusercontent.com/render/math?math=%24m%20%3D%20%5Clim_%7Bh%20%5Cto%200%7D%20%5Cfrac%7Bf(a%2Bh)-f(a)%7D%7Bh%7D%24>)
  - Or it can be ![$\lim_{\Delta x \to 0} \frac{\Delta y}{\Delta x} = \lim_{x_2 \to x_1} \frac{f(x_2)-f(x_1)}{x_2 - x_1} $](<https://render.githubusercontent.com/render/math?math=%24%5Clim_%7B%5CDelta%20x%20%5Cto%200%7D%20%5Cfrac%7B%5CDelta%20y%7D%7B%5CDelta%20x%7D%20%3D%20%5Clim_%7Bx_2%20%5Cto%20x_1%7D%20%5Cfrac%7Bf(x_2)-f(x_1)%7D%7Bx_2%20-%20x_1%7D%20%24>)
- The derivative of a function _f_ at a number _a_, denoted by ![$f'(a)$](<https://render.githubusercontent.com/render/math?math=%24f'(a)%24>) is ![$f'(a) = \lim_{h \to 0} \frac{f(a+h)-f(a)}{h}$](<https://render.githubusercontent.com/render/math?math=%24f'(a)%20%3D%20%5Clim_%7Bh%20%5Cto%200%7D%20%5Cfrac%7Bf(a%2Bh)-f(a)%7D%7Bh%7D%24>)
  - It is the function that returns the slope of the tangent as dependent variable.
  - It can also represent the instantaneous rate of change
  - The derivateve of a function can be also denoted as
    - ![$\frac{dx}{dy}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bdx%7D%7Bdy%7D%24)
    - ![$\frac{d}{dy}(y)$](<https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdy%7D(y)%24>)
    - ![$y'$](https://render.githubusercontent.com/render/math?math=%24y'%24)
    - ![$\dot{x}$](https://render.githubusercontent.com/render/math?math=%24%5Cdot%7Bx%7D%24) if _x_ represents time
- Higher Derivatives
  - The derivatives of a derivative is called the second derivative, it can be denoted as follows:
    - ![$\frac{d}{dy}\left(\frac{dy}{dx}\right)$](<https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdy%7D%5Cleft(%5Cfrac%7Bdy%7D%7Bdx%7D%5Cright)%24>)
    - ![$\frac{d^2 y}{d x^2}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%5E2%20y%7D%7Bd%20x%5E2%7D%24)
    - ![$f''(x)$](<https://render.githubusercontent.com/render/math?math=%24f''(x)%24>)
    - ![$y''$](https://render.githubusercontent.com/render/math?math=%24y''%24)
    - ![$\ddot{x}$](https://render.githubusercontent.com/render/math?math=%24%5Cddot%7Bx%7D%24)
  - Same idea for third and fourth and higher derivatives.
- A function _f_ is differentiable at a if _f'(a)_ exists. It is differen- tiable on an open interval (_a, b_)[or ![$(a, \infty)$](<https://render.githubusercontent.com/render/math?math=%24(a%2C%20%5Cinfty)%24>) or ![$(-\infty, a)$](<https://render.githubusercontent.com/render/math?math=%24(-%5Cinfty%2C%20a)%24>) or ![$(-\infty, \infty)$](<https://render.githubusercontent.com/render/math?math=%24(-%5Cinfty%2C%20%5Cinfty)%24>)] if it is differentiable at every number in the interval.

#### Rules

- Derivative of a Constant Function ![$\frac{d}{dx}(c)=0$](<https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D(c)%3D0%24>)
- The Power Rule - ![$\frac{d}{dx}(x^n)=nx^{n-1}$](<https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D(x%5En)%3Dnx%5E%7Bn-1%7D%24>)
- The Constant Multiple Rule - If _c_ is a constant and _f_ is a differentiable function, then ![$\frac{d}{dx}[cf(x)]=c \frac{d}{dx}f(x)$](<https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%5Bcf(x)%5D%3Dc%20%5Cfrac%7Bd%7D%7Bdx%7Df(x)%24>)
- The Sum Rule - If _f_ and _g_ are both differentiable, then ![$\frac{d}{dx}[f(x)+g(x)]= \frac{d}{dx}f(x)+\frac{d}{dx}g(x)$](<https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%5Bf(x)%2Bg(x)%5D%3D%20%5Cfrac%7Bd%7D%7Bdx%7Df(x)%2B%5Cfrac%7Bd%7D%7Bdx%7Dg(x)%24>)
- The Difference Rule - If _f_ and _g_ are both differentiable, then ![$\frac{d}{dx}[f(x)-g(x)]= \frac{d}{dx}f(x)-\frac{d}{dx}g(x)$](<https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%5Bf(x)-g(x)%5D%3D%20%5Cfrac%7Bd%7D%7Bdx%7Df(x)-%5Cfrac%7Bd%7D%7Bdx%7Dg(x)%24>)
- Derivative of the Natural Exponential Function - ![$\frac{d}{dx}(e^x)=e^x$](<https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D(e%5Ex)%3De%5Ex%24>)
- The Product Rule - If _f_ and _g_ are both differentiable, then ![$\frac{d}{dx}[f(x)g(x)]=f(x) \frac{d}{dx}[g(x)]+g(x) \frac{d}{dx}[f(x)]$](<https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%5Bf(x)g(x)%5D%3Df(x)%20%5Cfrac%7Bd%7D%7Bdx%7D%5Bg(x)%5D%2Bg(x)%20%5Cfrac%7Bd%7D%7Bdx%7D%5Bf(x)%5D%24>)
- The Quotient Rule - If _f_ and _g_ are differentiable, then ![$\frac{d}{dx}\left[\frac{f(x)}{g(x)}\right]=\frac{g(x) \frac{d}{dx}[f(x)]-f(x) \frac{d}{dx}[g(x)]}{[g(x)]^2}$](<https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%5Cleft%5B%5Cfrac%7Bf(x)%7D%7Bg(x)%7D%5Cright%5D%3D%5Cfrac%7Bg(x)%20%5Cfrac%7Bd%7D%7Bdx%7D%5Bf(x)%5D-f(x)%20%5Cfrac%7Bd%7D%7Bdx%7D%5Bg(x)%5D%7D%7B%5Bg(x)%5D%5E2%7D%24>)
- Derivatives of Trigonometric Functions
  - ![$\frac{d}{dx} (\sin x)=\cos x$](<https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%20(%5Csin%20x)%3D%5Ccos%20x%24>)
  - ![$\frac{d}{dx} (\cos x)=-\sin x$](<https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%20(%5Ccos%20x)%3D-%5Csin%20x%24>)
  - ![$\frac{d}{dx} (\tan x)=\sec^2 x$](<https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%20(%5Ctan%20x)%3D%5Csec%5E2%20x%24>)
  - ![$\frac{d}{dx} (\csc x)=-\csc x \cot x$](<https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%20(%5Ccsc%20x)%3D-%5Ccsc%20x%20%5Ccot%20x%24>)
  - ![$\frac{d}{dx} (\csc x)=-\csc x : \cot x$](<https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%20(%5Ccsc%20x)%3D-%5Ccsc%20x%20%5C%3A%20%5Ccot%20x%24>)
  - ![$\frac{d}{dx} (\sec x)=\sec x : \tan x$](<https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%20(%5Csec%20x)%3D%5Csec%20x%20%5C%3A%20%5Ctan%20x%24>)
  - ![$\frac{d}{dx} (\cot x)=-\csc^2 x$](<https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%20(%5Ccot%20x)%3D-%5Ccsc%5E2%20x%24>)

#### Theorem

- If _f_ is differentiable at _a_, then _f_ is continuous at _a_.

#### Related Solving Methods

# Linear Algebra

## Matrices

#### Definition of Matrices

- A Matrix is a representation of a system of linear equations.
  - ![$a_1x+b_1y=c_1$](https://render.githubusercontent.com/render/math?math=%24a_1x%2Bb_1y%3Dc_1%24) and ![$a_2x+b_2y=c_2$](https://render.githubusercontent.com/render/math?math=%24a_2x%2Bb_2y%3Dc_2%24) and be represented by a matrix as ![$\begin{bmatrix} a_1 & b_1 \ a_2 & b_2  \end{bmatrix}$](https://render.githubusercontent.com/render/math?math=%24%5Cbegin%7Bbmatrix%7D%20a_1%20%26%20b_1%20%5C%5C%20a_2%20%26%20b_2%20%20%5Cend%7Bbmatrix%7D%24)
- Augmented Matrix includes dependent variables of a system of linear equations in the right most column, ![$\begin{bmatrix} a_1 & b_1 & c_1 \ a_2 & b_2 & c_2  \end{bmatrix}$](https://render.githubusercontent.com/render/math?math=%24%5Cbegin%7Bbmatrix%7D%20a_1%20%26%20b_1%20%26%20c_1%20%5C%5C%20a_2%20%26%20b_2%20%26%20c_2%20%20%5Cend%7Bbmatrix%7D%24) or ![$\left[ \begin{array}{cc|r} a_1 & b_1 & c_1\ a_2 & b_2 & c_2 \end{array} \right]$](https://render.githubusercontent.com/render/math?math=%24%5Cleft%5B%20%5Cbegin%7Barray%7D%7Bcc%7Cr%7D%20a_1%20%26%20b_1%20%26%20c_1%5C%5C%20a_2%20%26%20b_2%20%26%20c_2%20%5Cend%7Barray%7D%20%5Cright%5D%24)
- The Size of A Matrix can be represented as `2 X 3`
  - First number represents the number of rows.(number of equations)
  - First number represents the number of columns.(number of variables)
- Square Matrix - is a matrix has the same number of rows and columns.
- The elements or entries of the matrix can be represented as ![$a_{ij}$](https://render.githubusercontent.com/render/math?math=%24a_%7Bij%7D%24) where `i` is its row number and `j` is its column number.
  - For example, ![$\begin{bmatrix} a_{11} & a_{12} & a_{13} \ a_{21} & a_{22} & a_{23} \ a_{31} & a_{32} & a_{33} \end{bmatrix}$](https://render.githubusercontent.com/render/math?math=%24%5Cbegin%7Bbmatrix%7D%20a_%7B11%7D%20%26%20a_%7B12%7D%20%26%20a_%7B13%7D%20%5C%5C%20a_%7B21%7D%20%26%20a_%7B22%7D%20%26%20a_%7B23%7D%20%5C%5C%20a_%7B31%7D%20%26%20a_%7B32%7D%20%26%20a_%7B33%7D%20%5Cend%7Bbmatrix%7D%24)
- For Matrix `A` and `B`, `A = B` if they have the same dimension and all their elements are the same.
- When a matrix add a matrix, a Matrix minus a matrix and a matrix multiply or divide by a constant. These operations will take effect on each element of the matrix independently.
  - For example, `A + B` will get Matrix `C` which all of its element equals the sum of elements of `A` and `B` from the same location.
  - These three operations of matrix can be combined and calculated at the same time.
  - Addition and Subtraction only works for two matrix that has the same dimension.
  - The dimension of matrices will not be changed by these operation.
- When a matrix multiply by a matrix. If Matrix `A` has shape `M X N`, If Matrix `B` has shape `P X Q`
  - `N` must equal `P`.
  - The result will be matrix `C` with shape `M X Q`.
  - matrix `C` will have element ![$c_{mq} = $](https://render.githubusercontent.com/render/math?math=%24c_%7Bmq%7D%20%3D%20%24) equals the sum of elements from row `m` of Matrix A multiplies elements from row `q` of Matrix B. Ex, ![$c_{mq} = a_{m1}b_{1q}+a_{m2}b_{2q}+ \ldots $](https://render.githubusercontent.com/render/math?math=%24c_%7Bmq%7D%20%3D%20a_%7Bm1%7Db_%7B1q%7D%2Ba_%7Bm2%7Db_%7B2q%7D%2B%20%5Cldots%20%24)
- Identity Matrix ![$I_n$](https://render.githubusercontent.com/render/math?math=%24I_n%24) is a `n X n` square matrix has 1 aross diagonal and 0 for all other elements.
- ![$A^{-1}$](https://render.githubusercontent.com/render/math?math=%24A%5E%7B-1%7D%24) is the inverse of matrix `A` if ![$A^{-1}A=AA^{-1}=I$](https://render.githubusercontent.com/render/math?math=%24A%5E%7B-1%7DA%3DAA%5E%7B-1%7D%3DI%24)
  - Find the inverse of a 2 by 2 matrix
    - if ![$A = \begin{bmatrix} a & b \ c & d \end{bmatrix}$](https://render.githubusercontent.com/render/math?math=%24A%20%3D%20%5Cbegin%7Bbmatrix%7D%20a%20%26%20b%20%5C%5C%20c%20%26%20d%20%5Cend%7Bbmatrix%7D%24) then ![$A^{-1} = \frac{1}{D} \begin{bmatrix} d & -b \ -c & a \end{bmatrix}$](https://render.githubusercontent.com/render/math?math=%24A%5E%7B-1%7D%20%3D%20%5Cfrac%7B1%7D%7BD%7D%20%5Cbegin%7Bbmatrix%7D%20d%20%26%20-b%20%5C%5C%20-c%20%26%20a%20%5Cend%7Bbmatrix%7D%24) where `D` is the determinat of `A` ![$D = ad-bc$](https://render.githubusercontent.com/render/math?math=%24D%20%3D%20ad-bc%24)
  - Find the inverse of any matrices by using Gaussian Elimination
    - If ![$A=\begin{bmatrix} a & b \ c & d \end{bmatrix}$](https://render.githubusercontent.com/render/math?math=%24A%3D%5Cbegin%7Bbmatrix%7D%20a%20%26%20b%20%5C%5C%20c%20%26%20d%20%5Cend%7Bbmatrix%7D%24)
    - Convert the matrix A on the left side to Identity matrix then the inverse matrix will be the matrix on the right side. ![$\left[ \begin{array}{cc|rr} a & b & 1 & 0 \ c & d & 0 & 1 \end{array} \right] \Rightarrow [I : | ; A^{-1}]$](https://render.githubusercontent.com/render/math?math=%24%5Cleft%5B%20%5Cbegin%7Barray%7D%7Bcc%7Crr%7D%20a%20%26%20b%20%26%201%20%26%200%20%5C%5C%20c%20%26%20d%20%26%200%20%26%201%20%5Cend%7Barray%7D%20%5Cright%5D%20%5CRightarrow%20%5BI%20%5C%3A%20%7C%20%5C%3B%20A%5E%7B-1%7D%5D%24)
- Matrix `A` divide by `B` equals to `A` times the inverse of `B`.
  - A system of linear equations can be represent by `AX = B` where `A` is a matrix of coefficient, `X` is a `n` by 1 matrix n variables, `C` equals a `n` by 1 matrix of the values of the dependent variables. Then `X` can be solved by using `B` times the inverse of `A`.
- The determinant of a matrix is a single value calculated from all elements of the matrix.
  - The determinant of a matrix `A` can be represented as `|A|` or `det(A)`
  - For a `2 X 2` matrix ![$A = \begin{bmatrix} a & b \ c & d \end{bmatrix}$](https://render.githubusercontent.com/render/math?math=%24A%20%3D%20%5Cbegin%7Bbmatrix%7D%20a%20%26%20b%20%5C%5C%20c%20%26%20d%20%5Cend%7Bbmatrix%7D%24), the determinant equals to `ad - bc`.
  - For a `3 X 3` matrix to get the determinant, expand two more new column to the right, copy first column as the fourth column, copy the second column as the fifth column. and draw all the possible diagonal lines in two direction. Multiple all elements on one diagonal lines, add the sum of diagonal elements that goes from top-left to bottom right, substract the sum of diagonal elements that goes from top-right to bottom left.
    - Same idea for matrices with larger sizes.
  - coefficient + - + method

#### Gaussian Elimination

- Row Echelon Form - It has 1 across diagonal, all entries below 1 is 0.
  - In an augmented matrix, independent variables can be solved by subsitution.
- Reduced Echelon form - has 1 across diagonal, all other entries are 0.
  - In an augmented matrix, independent variables is solved and equals to corresponding entries in the right most coloumn.
- Method of Gaussian Elimination - Solve a system of linear equations by finding the Row Echelon Form or Reduced Echelon Form of an augmented matrix.
  - Steps for finding the Row Echelon Form
    - Divide the entire row by the first element to make the first element on first row 1.
    - Multiply first row and Substitute to the second row so the first element of the second row is 0.
    - repeat the step for the next row until the matrix is in the Row Echelon Form
  - Steps for finding the Reduced Echelon Form
    - find the Row Echelon Form first.
    - multiply and subsitute the last row into the second last row to make the last element of the second last row 0.
    - Transform the upper rows step by step until the matrix become Reduced Echelon Form.
  - ![$\left[ \begin{array}{ccc|r} 1 & 2 & 2 & 3 \ 0 & 1 & 1 & 2 \ 0 & 0 & 0 & 2 \end{array} \right]$](https://render.githubusercontent.com/render/math?math=%24%5Cleft%5B%20%5Cbegin%7Barray%7D%7Bccc%7Cr%7D%201%20%26%202%20%26%202%20%26%203%20%5C%5C%200%20%26%201%20%26%201%20%26%202%20%5C%5C%200%20%26%200%20%26%200%20%26%202%20%5Cend%7Barray%7D%20%5Cright%5D%24) this system of linear equations has no solution, because ![$0x+0y+0z \neq 2$](https://render.githubusercontent.com/render/math?math=%240x%2B0y%2B0z%20%5Cneq%202%24)
  - In Echelon Form if one row are all 0s, the equation has inifite solutions.

#### Cramer's Rule

- For a system of linear equations `D` is the determinant of the matrix of coefficient. ![$D_x$](https://render.githubusercontent.com/render/math?math=%24D_x%24) is the determinant of the matrix of coefficient which the column for coefficient of `x` is replaced by the dependent variable matrix. ![$D_y$](https://render.githubusercontent.com/render/math?math=%24D_x%24) is the determinant of the matrix of coefficient which the column for coefficient of `y` is replaced by the dependent variable matrix, and so on. Then ![$x= \frac{D_x}{D}, y= \frac{D_y}{D}, \ldots$](https://render.githubusercontent.com/render/math?math=%24x%3D%20%5Cfrac%7BD_x%7D%7BD%7D%2C%20y%3D%20%5Cfrac%7BD_y%7D%7BD%7D%2C%20%5Cldots%24)

# Probability

# Statistics
