# Calculus

## Limit

#### Definition

- Intuitive Definitions
  - Definition of a Limit
    - Suppose _`f(x)`_ is defined when `x` is near the number `a`. (This means that f is defined on some open interval that contains a, except possibly at a itself.) Then we write ![$\lim_{x \to a}f(x)=L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df%28x%29%3DL%24) and say "the limit of `f(x)`, as x approaches a, equals L" if we can make the values of _`f(x)`_ arbitrarily close to L (as close to L as we like) by restricting x to be sufficiently close to a (on either side of a) but not equal to a.
  - Definition of One-Sided Limits
    - ![$\lim_{x \to a^-}f(x)=L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E-%7Df%28x%29%3DL%24) and say the left-hand limit of _`f(x)`_ as x approaches a [or the limit of f sxd as x approaches `a` from the left] is equal to `L` if we can make the values of _`f(x)`_ arbitrarily close to `L` by taking `x` to be sufficiently close to a with `x` less than `a`.
    - ![$\lim_{x \to a^+}f(x)=L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E%2B%7Df%28x%29%3DL%24) if we require that x be greater than a, we get "the right-hand limit of _`f(x)`_ as `x` approaches `a` is equal to `L`".
  - Definition of an Infinite Limit
    - Let `f` be a function defined on both sides of `a`, except possibly at `a` itself. Then ![$\lim_{x \to a}f(x)= \infty$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df%28x%29%3D%20%5Cinfty%24) means that the values of _`f(x)`_ can be made arbitrarily large (as large as we please) by taking `x` sufficiently close to `a`, but not equal to `a`.
    - Let `f` be a function defined on both sides of `a`, except possibly at `a` itself. Then ![$\lim_{x \to a}f(x)= - \infty$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df%28x%29%3D%20-%20%5Cinfty%24) means that the values of _`f(x)`_ can be made arbitrarily large negative by taking `x` sufficiently close to `a`, but not equal to `a`.
  - Definition of a Limit at Infinity
    - Let _f_ be a function defined on some interval ![$(a, \infty)$](https://render.githubusercontent.com/render/math?math=%24(a%2C%20%5Cinfty%29%24). Then ![$\lim_{x \to \infty}f(x)= L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20%5Cinfty%7Df%28x%29%3D%20L%24) means that the values of _f(x)_ can be made arbitrarily close to _L_ by requiring _x_ to be sufficiently large.
    - Let _f_ be a function defined on some interval ![$(a, -\infty)$](https://render.githubusercontent.com/render/math?math=%24%28a%2C%20-%5Cinfty%29%24). Then ![$\lim_{x \to - \infty}f(x)= L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20-%20%5Cinfty%7Df%28x%29%3D%20L%24) means that the values of _f(x)_ can be made arbitrarily close to _L_ by requiring _x_ to be sufficiently large negative.
  - Definition of an Infinite Limit at Infinity
    - Let _f_ be a function defined on some interval ![$(a, \infty)$](https://render.githubusercontent.com/render/math?math=%24%28a%2C%20%5Cinfty%29%24). Then ![$\lim_{x \to \infty}f(x)= \infty$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20%5Cinfty%7Df%28x%29%3D%20%5Cinfty%24) means that for every positive number _M_ there is a corresponding positive number _N_ such that if ![$x > N$](https://render.githubusercontent.com/render/math?math=%24x%20%3E%20N%24) then ![$f(x) > M$](https://render.githubusercontent.com/render/math?math=%24f%28x%29%20%3E%20M%24)
- Precise Definitions
  - Definition of a Limit
    - Let _`f`_ be a function defined on some open interval that contains the number _`a`_, except possibly at _`a`_ itself. Then we say that the limit of _`f(x)`_ as _`x`_ approaches _`a`_ is _`L`_, and we write ![$\lim_{x \to a}f(x) = L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df%28x%29%20%3D%20L%24) if for every number ![$\epsilon > 0$](https://render.githubusercontent.com/render/math?math=%24%5Cepsilon%20%3E%200%24) there is a number ![$\delta > 0$](https://render.githubusercontent.com/render/math?math=%24%5Cdelta%20%3E%200%24) such that, if ![$0 < |x-a| < \delta$](https://render.githubusercontent.com/render/math?math=%240%20%3C%20%7Cx-a%7C%20%3C%20%5Cdelta%24) then ![$|f(x) - L| < \epsilon$](https://render.githubusercontent.com/render/math?math=%24%7Cf%28x%29%20-%20L%7C%20%3C%20%5Cepsilon%24)
  - Definition of One-Sided Limits
    - ![$\lim_{x \to a^-}f(x) = L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E-%7Df%28x%29%20%3D%20L%24) if for every number ![$\epsilon > 0$](https://render.githubusercontent.com/render/math?math=%24%5Cepsilon%20%3E%200%24) there is a number ![$\delta > 0$](https://render.githubusercontent.com/render/math?math=%24%5Cdelta%20%3E%200%24) such that, if ![$a - \delta < x < a$](https://render.githubusercontent.com/render/math?math=%24a%20-%20%5Cdelta%20%3C%20x%20%3C%20a%24) then ![$|f(x) - L| < \epsilon$](https://render.githubusercontent.com/render/math?math=%24%7Cf%28x%29%20-%20L%7C%20%3C%20%5Cepsilon%24)
    - ![$\lim_{x \to a^-}f(x) = L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E-%7Df%28x%29%20%3D%20L%24) if for every number ![$\epsilon > 0$](https://render.githubusercontent.com/render/math?math=%24%5Cepsilon%20%3E%200%24) there is a number ![$\delta > 0$](https://render.githubusercontent.com/render/math?math=%24%5Cdelta%20%3E%200%24) such that, if ![$a < x < a + \delta $](https://render.githubusercontent.com/render/math?math=%24a%20%3C%20x%20%3C%20a%20%2B%20%5Cdelta%20%24) then ![$|f(x) - L| < \epsilon$](https://render.githubusercontent.com/render/math?math=%24%7Cf%28x%29%20-%20L%7C%20%3C%20%5Cepsilon%24)
  - Definition of an Infinite Limit
    - Let _`f`_ be a function defined on some open interval that contains the number _`a`_, except possibly at _`a`_ itself. Then ![$\lim_{x \to a}f(x) = \infty$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df%28x%29%20%3D%20%5Cinfty%24) means that for every positive number _M_ there is a positive number ![$\delta$](https://render.githubusercontent.com/render/math?math=%24%5Cdelta%24) such that if ![$0 < |x-a| < \delta$](https://render.githubusercontent.com/render/math?math=%240%20%3C%20%7Cx-a%7C%20%3C%20%5Cdelta%24) then ![$f(x) > M$](https://render.githubusercontent.com/render/math?math=%24f%28x%29%20%3E%20M%24)
    - Let _`f`_ be a function defined on some open interval that contains the number _`a`_, except possibly at _`a`_ itself. Then ![$\lim_{x \to a}f(x) = - \infty$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df%28x%29%20%3D%20-%20%5Cinfty%24) means that for every positive number _M_ there is a negetive number ![$\delta$](https://render.githubusercontent.com/render/math?math=%24%5Cdelta%24) such that if ![$0 < |x-a| < \delta$](https://render.githubusercontent.com/render/math?math=%240%20%3C%20%7Cx-a%7C%20%3C%20%5Cdelta%24) then ![$f(x) < N$](https://render.githubusercontent.com/render/math?math=%24f%28x%29%20%3C%20N%24)
  - Definition of a Limit at Infinity - Let _f_ be a function defined on some interval ![$(a, \infty)$](https://render.githubusercontent.com/render/math?math=%24%28a%2C%20%5Cinfty%29%24). Then ![$\lim_{x \to \infty} f(x) = L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20%5Cinfty%7D%20f%28x%29%20%3D%20L%24) means that for every ![$\epsilon > 0$](https://render.githubusercontent.com/render/math?math=%24%5Cepsilon%20%3E%200%24) there is a corresponding number _N_ such that if ![$x > N$](https://render.githubusercontent.com/render/math?math=%24x%20%3E%20N%24) then ![$| f(x) - L| < \epsilon$](https://render.githubusercontent.com/render/math?math=%24%7C%20f%28x%29%20-%20L%7C%20%3C%20%5Cepsilon%24) - Let _f_ be a function defined on some interval ![$(-\infty , a)$](https://render.githubusercontent.com/render/math?math=%24%28-%5Cinfty%20%2C%20a%29%24). Then ![$\lim_{x \to -\infty} f(x) = L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20-%5Cinfty%7D%20f%28x%29%20%3D%20L%24) means that for every ![$\epsilon > 0$](https://render.githubusercontent.com/render/math?math=%24%5Cepsilon%20%3E%200%24) there is a corresponding number _N_ such that if ![$x < N$](https://render.githubusercontent.com/render/math?math=%24x%20%3C%20N%24) then ![$| f(x) - L| < \epsilon$](https://render.githubusercontent.com/render/math?math=%24%7C%20f%28x%29%20-%20L%7C%20%3C%20%5Cepsilon%24)
- ![$\lim_{x \to a}f(x)=L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df%28x%29%3DL%24) if and only if ![$\lim_{x \to a^+}f(x)=L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E%2B%7Df%28x%29%3DL%24) and ![$\lim_{x \to a^-}f(x)=L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E-%7Df%28x%29%3DL%24)
- The vertical line `x = a` is called a vertical asymptote of the curve ![$y= f(x)$](https://render.githubusercontent.com/render/math?math=%24y%3D%20f%28x%29%24) if at least one of the following statements is true:
  - ![$\lim_{x \to a}f(x)= \infty$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df%28x%29%3D%20%5Cinfty%24)
  - ![$\lim_{x \to a^-}f(x)= \infty$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E-%7Df%28x%29%3D%20%5Cinfty%24)
  - ![$\lim_{x \to a^+}f(x)= \infty$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E%2B%7Df%28x%29%3D%20%5Cinfty%24)
  - ![$\lim_{x \to a}f(x)=- \infty$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df%28x%29%3D-%20%5Cinfty%24)
  - ![$\lim_{x \to a^-}f(x)=- \infty$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E-%7Df%28x%29%3D-%20%5Cinfty%24)
  - ![$\lim_{x \to a^+}f(x)=- \infty$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E%2B%7Df%28x%29%3D-%20%5Cinfty%24)
  - Example: ![$\lim_{x \to 0^+} \ln{x}=- \infty$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%200%5E%2B%7D%20%5Cln%7Bx%7D%3D-%20%5Cinfty%24)
- the line _y = mx + b_ is called a slant(oblique) asymptote where ![$\lim_{x \to \infty} [f(x)-(mx+b)]=0$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20%5Cinfty%7D%20%5Bf%28x%29-%28mx%2Bb%29%5D%3D0%24) if ![$m \neq 0$](https://render.githubusercontent.com/render/math?math=%24m%20%5Cneq%200%24)
- A function _f_ is continuous at a number a if ![$\lim_{x \to a}f(x) = f(a)$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df%28x%29%20%3D%20f%28a%29%24)
- A function _f_ is continuous from the right at a number _a_ if ![$\lim_{x \to a^+}f(x) = f(a)$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E%2B%7Df(x%29%20%3D%20f(a%29%24)
- A function _f_ is continuous from the left at a number _a_ if ![$\lim_{x \to a^-}f(x) = f(a)$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E-%7Df(x%29%20%3D%20f(a%29%24)
- A function _f_ is continuous on an interval if it is continuous at every number in the interval. (If _f_ is defined only on one side of an endpoint of the interval, we understand continuous at the endpoint to mean continuous from the right or continuous from the left.)
- The line _y = L_ is called a horizontal asymptote of the curve _y = f(x)_ if either ![$\lim_{x \to a}f(x)= - \infty$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x%29%3D%20-%20%5Cinfty%24) or ![$(a, -\infty)$](https://render.githubusercontent.com/render/math?math=%24(a%2C%20-%5Cinfty%29%24). Then ![$\lim_{x \to - \infty}f(x)= L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20-%20%5Cinfty%7Df(x%29%3D%20L%24)
  - For Example:
    - ![$\lim_{x \to - \infty}\tan^{-1}{x}= - \frac{\pi}{2} $](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20-%20%5Cinfty%7D%5Ctan%5E%7B-1%7D%7Bx%7D%3D%20-%20%5Cfrac%7B%5Cpi%7D%7B2%7D%20%24)
    - ![$\lim_{x \to \infty}\tan^{-1}{x}= \frac{\pi}{2} $](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20%5Cinfty%7D%5Ctan%5E%7B-1%7D%7Bx%7D%3D%20%5Cfrac%7B%5Cpi%7D%7B2%7D%20%24)
    - ![$\lim_{x \to - \infty} e^x = 0$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20-%20%5Cinfty%7D%20e%5Ex%20%3D%200%24)
- Definition of the Number _e_
  - _e_ is the number such that ![$\lim_{h \to 0} \frac{e^h-1}{h} = 1$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bh%20%5Cto%200%7D%20%5Cfrac%7Be%5Eh-1%7D%7Bh%7D%20%3D%201%24)
  - So, ![$e = \lim_{x \to 0} (1+x)^{\frac{1}{x}}$](https://render.githubusercontent.com/render/math?math=%24e%20%3D%20%5Clim_%7Bx%20%5Cto%200%7D%20(1%2Bx%29%5E%7B%5Cfrac%7B1%7D%7Bx%7D%7D%24) or ![$e = \lim_{x \to \infty} \left(1+ \frac{1}{n}\right)^n$](https://render.githubusercontent.com/render/math?math=%24e%20%3D%20%5Clim_%7Bx%20%5Cto%20%5Cinfty%7D%20%5Cleft(1%2B%20%5Cfrac%7B1%7D%7Bn%7D%5Cright%29%5En%24)
- L'Hospital's Rule - Suppose _f_ and _t_ are differentiable and ![$g'(x) \neq 0$](https://render.githubusercontent.com/render/math?math=%24g'(x%29%20%5Cneq%200%24) on an open interval _I_ that contains _a_ (except possibly at _a_). Suppose that ![$\lim_{x \to a}f(x) = 0$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x%29%20%3D%200%24) and ![$\lim_{x \to a}g(x) = 0$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Dg(x%29%20%3D%200%24) or that ![$\lim_{x \to a}f(x) = \pm \infty$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x%29%20%3D%20%5Cpm%20%5Cinfty%24) and ![$\lim_{x \to a}g(x) = \pm \infty$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Dg(x%29%20%3D%20%5Cpm%20%5Cinfty%24) In other words, we have an indeterminate form of type 0/0 or ![$\infty / \infty$](https://render.githubusercontent.com/render/math?math=%24%5Cinfty%20%2F%20%5Cinfty%24). Then ![$\lim_{x \to a} \frac{f(x)}{g(x)}=\lim_{x \to a} \frac{f'(x)}{g'(x)}$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20%5Cfrac%7Bf(x%29%7D%7Bg(x%29%7D%3D%5Clim_%7Bx%20%5Cto%20a%7D%20%5Cfrac%7Bf'(x%29%7D%7Bg'(x%29%7D%24) if the limit on the right side exists (or is opposite/negative inifinity)

#### Laws

- Limit Laws, Suppose that `c` is a constant and the limits ![$\lim_{x \to a} f(x)$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20f(x%29%24) and ![$\lim_{x \to a} g(x)$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20g(x%29%24) exist. Then:
  - ![$\lim_{x \to a} [f(x)+g(x)]=\lim_{x \to a} f(x)+\lim_{x \to a} g(x)$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20%5Bf(x%29%2Bg(x%29%5D%3D%5Clim_%7Bx%20%5Cto%20a%7D%20f(x%29%2B%5Clim_%7Bx%20%5Cto%20a%7D%20g(x%29%24) Sum Law
  - ![$\lim_{x \to a} [f(x)-g(x)]=\lim_{x \to a} f(x)-\lim_{x \to a} g(x)$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20%5Bf(x%29-g(x%29%5D%3D%5Clim_%7Bx%20%5Cto%20a%7D%20f(x%29-%5Clim_%7Bx%20%5Cto%20a%7D%20g(x%29%24) Difference Law
  - ![$\lim_{x \to a} [cf(x)]=c \lim_{x \to a} f(x)$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20%5Bcf(x%29%5D%3Dc%20%5Clim_%7Bx%20%5Cto%20a%7D%20f(x%29%24) Constant Multiple Law
  - ![$\lim_{x \to a} [f(x)g(x)]=\lim_{x \to a} f(x) \cdot \lim_{x \to a} g(x)$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20%5Bf(x%29g(x%29%5D%3D%5Clim_%7Bx%20%5Cto%20a%7D%20f(x%29%20%5Ccdot%20%5Clim_%7Bx%20%5Cto%20a%7D%20g(x%29%24) Product Law
  - ![$\lim_{x \to a} \frac{f(x)}{g(x)}=\frac{\lim_{x \to a} f(x)}{\lim_{x \to a} g(x)}$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20%5Cfrac%7Bf(x%29%7D%7Bg(x%29%7D%3D%5Cfrac%7B%5Clim_%7Bx%20%5Cto%20a%7D%20f(x%29%7D%7B%5Clim_%7Bx%20%5Cto%20a%7D%20g(x%29%7D%24) if ![$\lim_{x \to a} g(x) \neq 0$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20g(x%29%20%5Cneq%200%24) Quotient Law
  - ![$\lim_{x \to a} [f(x)]^n = \left[\lim_{x \to a} f(x)\right]^n$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20%5Bf(x%29%5D%5En%20%3D%20%5Cleft%5B%5Clim_%7Bx%20%5Cto%20a%7D%20f(x%29%5Cright%5D%5En%24) where n is a positive integer, Power Law
  - ![$\lim_{x \to a}c=c $](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Dc%3Dc%20%24)
  - ![$\lim_{x \to a}x=a $](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Dx%3Da%20%24)
  - ![$\lim_{x \to a} x^n=a^n $](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20x%5En%3Da%5En%20%24) where n is a positive integer
  - ![$\lim_{x \to a} \sqrt[n]{x}=\sqrt[n]{a} $](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20%5Csqrt%5Bn%5D%7Bx%7D%3D%5Csqrt%5Bn%5D%7Ba%7D%20%24) where `n` is a positive integer (If `n` is even, we assume that `a > 0`.)
  - ![$\lim_{x \to a} \sqrt[n]{f(x)}=\sqrt[n]{\lim_{x \to a} f(x)} $](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%20%5Csqrt%5Bn%5D%7Bf(x%29%7D%3D%5Csqrt%5Bn%5D%7B%5Clim_%7Bx%20%5Cto%20a%7D%20f(x%29%7D%20%24) where `n` is a positive integer. If `n` is even, we assume that ![$\lim_{x \to a}f(x) > 0$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x%29%20%3E%200%24). Root Law

#### Properties

- Direct Substitution Property If _`f`_ is a polynomial or a rational function and _`a`_ is in the domain of _`f`_ , then ![$\lim_{x \to a}f(x) = f(a)$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x%29%20%3D%20f(a%29%24)
- If ![$f(x)=g(x)$](https://render.githubusercontent.com/render/math?math=%24f(x%29%3Dg(x%29%24) when ![$x \neq a$](https://render.githubusercontent.com/render/math?math=%24x%20%5Cneq%20a%24), then ![$\lim_{x \to a}f(x) = \lim_{x \to a}g(x)$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x%29%20%3D%20%5Clim_%7Bx%20%5Cto%20a%7Dg(x%29%24) provided the limits exist.

#### Theorem

- ![$\lim_{x \to a}f(x) = L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x%29%20%3D%20L%24) if and only if ![$\lim_{x \to a_-}f(x) = L = \lim_{x \to a_+}f(x)$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a_-%7Df(x%29%20%3D%20L%20%3D%20%5Clim_%7Bx%20%5Cto%20a_%2B%7Df(x%29%24)
- If ![$f(x) \leqslant g(x)$](https://render.githubusercontent.com/render/math?math=%24f(x%29%20%5Cleqslant%20g(x%29%24) where _`x`_ is near _`a`_ (except possibly at _`a`_) and the limits of _`f`_ and _`g`_ both exist as _`x`_ approaches _`a`_, then ![$\lim_{x \to a}f(x) \leqslant \lim_{x \to a}g(x)$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x%29%20%5Cleqslant%20%5Clim_%7Bx%20%5Cto%20a%7Dg(x%29%24)
- The Squeeze Theorem - If ![$f(x) \leqslant g(x) \leqslant h(x)$](https://render.githubusercontent.com/render/math?math=%24f(x%29%20%5Cleqslant%20g(x%29%20%5Cleqslant%20h(x%29%24) when _`x`_ is near _`a`_ (except possibly at _`a`_) and ![$\lim_{x \to a}f(x)= \lim_{x \to a}h(x) = L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(x%29%3D%20%5Clim_%7Bx%20%5Cto%20a%7Dh(x%29%20%3D%20L%24) then ![$\lim_{x \to a}g(x) = L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Dg(x%29%20%3D%20L%24)
- If _f_ and _g_ are continuous at _a_ and _c_ is a constant, then the following functions are also continuous at _a_:
  - _f + g_
  - _f - g_
  - _cf_
  - _fg_
  - ![$\frac{f}{g}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bf%7D%7Bg%7D%24) if ![$g(a) \neq 0$](https://render.githubusercontent.com/render/math?math=%24g(a%29%20%5Cneq%200%24)
- Any polynomial is continuous everywhere; that is, it is continuous on ![$\mathbb{R} = (- \infty, \infty)$](https://render.githubusercontent.com/render/math?math=%24%5Cmathbb%7BR%7D%20%3D%20(-%20%5Cinfty%2C%20%5Cinfty%29%24).
- Any rational function is continuous wherever it is defined; that is, it is contin- uous on its domain.
- The following types of functions are continuous at every number in their domains:
  - polynomials
  - rational functions
  - root functions
  - trigonometric functions
  - exponential functions
  - inverse trigonometric functions
  - logarithmic functions
- If _f_ is continuous at _b_ and ![$\lim_{x \to a}g(x) = b$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Dg(x%29%20%3D%20b%24)
  - then ![$\lim_{x \to a}f(g(x)) =f(b)$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(g(x%29%29%20%3Df(b%29%24).
  - In other words, ![$\lim_{x \to a}f(g(x)) =f\left(\lim_{x \to a}g(x)\right)$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7Df(g(x%29%29%20%3Df%5Cleft(%5Clim_%7Bx%20%5Cto%20a%7Dg(x%29%5Cright%29%24)
- If _g_ is continuous at _a_ and _f_ is continuous at _g(a)_, then the composite function ![$f \circ g$](https://render.githubusercontent.com/render/math?math=%24f%20%5Ccirc%20g%24) given by ![$(f \circ g)(x) = f(g(x))$](https://render.githubusercontent.com/render/math?math=%24(f%20%5Ccirc%20g%29(x%29%20%3D%20f(g(x%29%29%24) is continuous at _a_.
- The Intermediate Value Theorem - Suppose that _f_ is continuous on the closed interval ![$[a,b]$](https://render.githubusercontent.com/render/math?math=%24%5Ba%2Cb%5D%24) and let _N_ be any number between _f(a)_ and _f(b)_ , where ![$f(a) \neq f(b)$](https://render.githubusercontent.com/render/math?math=%24f(a%29%20%5Cneq%20f(b%29%24). Then there exists _a_ number _c_ in ![$(a,b)$](https://render.githubusercontent.com/render/math?math=%24(a%2Cb%29%24) such that _f(c) = N_.
- If ![$r > 0$](https://render.githubusercontent.com/render/math?math=%24r%20%3E%200%24) is a rational number, then ![$\lim_{x \to \infty}\frac{1}{x^r}= 0$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20%5Cinfty%7D%5Cfrac%7B1%7D%7Bx%5Er%7D%3D%200%24) If ![$r > 0$](https://render.githubusercontent.com/render/math?math=%24r%20%3E%200%24) is a rational number such that ![$x^r$](https://render.githubusercontent.com/render/math?math=%24x%5Er%24) is defined for all _x_, then ![$\lim_{x \to - \infty}\frac{1}{x^r}= 0$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20-%20%5Cinfty%7D%5Cfrac%7B1%7D%7Bx%5Er%7D%3D%200%24)

#### Related Solving Methods

- use _f_ over the recipical of _g_ for Indeterminate products, in order to use the L'Hospital's Rule.

## Derivatives

#### Definition

- Tangent Line - The tangent line to the curve ![$y = f(x)$](https://render.githubusercontent.com/render/math?math=%24y%20%3D%20f(x%29%24)
  - at the point ![$P(a, f(a))$](https://render.githubusercontent.com/render/math?math=%24P(a%2C%20f(a%29%29%24) is the line through _P_ with slope ![$m = \lim_{x \to a} \frac{f(x)-f(a)}{x-a}$](https://render.githubusercontent.com/render/math?math=%24m%20%3D%20%5Clim_%7Bx%20%5Cto%20a%7D%20%5Cfrac%7Bf(x%29-f(a%29%7D%7Bx-a%7D%24) provided that this limit exists.
  - Optionally, ![$m = \lim_{h \to 0} \frac{f(a+h)-f(a)}{h}$](https://render.githubusercontent.com/render/math?math=%24m%20%3D%20%5Clim_%7Bh%20%5Cto%200%7D%20%5Cfrac%7Bf(a%2Bh%29-f(a%29%7D%7Bh%7D%24)
  - Or it can be ![$\lim_{\Delta x \to 0} \frac{\Delta y}{\Delta x} = \lim_{x_2 \to x_1} \frac{f(x_2)-f(x_1)}{x_2 - x_1} $](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7B%5CDelta%20x%20%5Cto%200%7D%20%5Cfrac%7B%5CDelta%20y%7D%7B%5CDelta%20x%7D%20%3D%20%5Clim_%7Bx_2%20%5Cto%20x_1%7D%20%5Cfrac%7Bf(x_2%29-f(x_1%29%7D%7Bx_2%20-%20x_1%7D%20%24)
- The derivative of a function _f_ at a number _a_, denoted by ![$f'(a)$](https://render.githubusercontent.com/render/math?math=%24f'(a%29%24) is ![$f'(a) = \lim_{h \to 0} \frac{f(a+h)-f(a)}{h}$](https://render.githubusercontent.com/render/math?math=%24f'(a%29%20%3D%20%5Clim_%7Bh%20%5Cto%200%7D%20%5Cfrac%7Bf(a%2Bh%29-f(a%29%7D%7Bh%7D%24)
  - It is the function that returns the slope of the tangent as dependent variable.
  - It can also represent the instantaneous rate of change.
  - The derivateve of a function can be also denoted as
    - ![$\frac{dy}{dx}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bdy%7D%7Bdx%7D%24), known as Leibniz notation.
      - Does not have to be `dy` over `dx`, anything below is the current independent variable.
      - The notation itself can be calculated since it represent a relationship in fraction notation. For example, `dy/dx = (dy/dz)/(dx/dz)`
    - ![$\frac{d}{dx}(x)$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D(x%29%24)
    - ![$y'$](https://render.githubusercontent.com/render/math?math=%24y'%24)
    - ![$\dot{x}$](https://render.githubusercontent.com/render/math?math=%24%5Cdot%7Bx%7D%24) if _x_ represents time
    - All of the notation represents how much `y` changes when `x` changes.
- Higher Derivatives
  - The derivatives of a derivative is called the second derivative, it can be denoted as follows:
    - ![$\frac{d}{dy}\left(\frac{dy}{dx}\right)$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdy%7D%5Cleft(%5Cfrac%7Bdy%7D%7Bdx%7D%5Cright%29%24)
    - ![$\frac{d^2 y}{d x^2}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%5E2%20y%7D%7Bd%20x%5E2%7D%24)
    - ![$f''(x)$](https://render.githubusercontent.com/render/math?math=%24f''(x%29%24)
    - ![$y''$](https://render.githubusercontent.com/render/math?math=%24y''%24)
    - ![$\ddot{x}$](https://render.githubusercontent.com/render/math?math=%24%5Cddot%7Bx%7D%24)
  - Same idea for third and fourth and higher derivatives.
- A function _f_ is differentiable at a if _f'(a)_ exists. It is differen- tiable on an open interval (_a, b_)[or ![$(a, \infty)$](https://render.githubusercontent.com/render/math?math=%24(a%2C%20%5Cinfty%29%24) or ![$(-\infty, a)$](https://render.githubusercontent.com/render/math?math=%24(-%5Cinfty%2C%20a%29%24) or ![$(-\infty, \infty)$](https://render.githubusercontent.com/render/math?math=%24(-%5Cinfty%2C%20%5Cinfty%29%24)] if it is differentiable at every number in the interval.
- Let _c_ be a number in the domain _D_ of a function _f_. Then _f(c)_ is the
  - absolute maximum value of _f_ on _D_ if ![$f(c) \geqslant f(x)$](https://render.githubusercontent.com/render/math?math=%24f(c%29%20%5Cgeqslant%20f(x%29%24) for all _x_ in _D_.
  - absolute minimum value of f on D if ![$f(c) \leqslant f(x)$](https://render.githubusercontent.com/render/math?math=%24f(c%29%20%5Cleqslant%20f(x%29%24) for all _x_ in _D_.
- The number _f(c)_ is a
  - local maximum value of _f_ if ![$f(c) \geqslant f(x)$](https://render.githubusercontent.com/render/math?math=%24f(c%29%20%5Cgeqslant%20f(x%29%24) when _x_ is near _c_.
  - local maximum value of _f_ if ![$f(c) \leqslant f(x)$](https://render.githubusercontent.com/render/math?math=%24f(c%29%20%5Cleqslant%20f(x%29%24) when _x_ is near _c_.
- A critical number of a function _f_ is a number _c_ in the domain of _f_ such that either _f'(c) = 0_ or _f'(c)_ does not exist.
  - If _f_ has a local maximum or minimum at _c_, then _c_ is a critical number of _f_.
- If the graph of _f_ lies above all of its tangents on an interval _I_, then it is called concave upward on _I_. If the graph of _f_ lies below all of its tangents on _I_, it is called concave downward on _I_.
- A point _P_ on a curve _y = f(x)_ is called an inflection point if _f_ is continuous there and the curve changes from concave upward to concave downward or from concave downward to concave upward at _P_.
- A function _F_ is called an antiderivative of _f_ on an interval _I_ if `F'(x)=f(x)` for all _x_ in _I_.
- The derivative of polar functions
  - Polar coordinates uses the distance to origin and the angle `θ` between the line to origin and x-axis to represent the location of a point. Instead of using `x`, `y` values in Cartesian coordinates.
  - When converting a point from cartesian coordinates to polar coordinates, ![$r = \sqrt{x^2+y^2}$](https://render.githubusercontent.com/render/math?math=%24r+%3D+%5Csqrt%7Bx%5E2%2By%5E2%7D%24) and ![$\theta = \tan^{-1}{\left(\frac{y}{x}\right )}$](https://render.githubusercontent.com/render/math?math=%24%5Ctheta+%3D+%5Ctan%5E%7B-1%7D%7B%5Cleft%28%5Cfrac%7By%7D%7Bx%7D%5Cright+%29%7D%24)
  - When converting a point from polar coordinates to cartesian coordinates, _`x = rsinθ`_ and _`y = rcosθ`_
  - Then function that uses `θ` as its indenpendent variable and `r` as its dependent variable are called polar function.
    - Using selected `θ` value to graph the polar function. polar function simplfy problem related to functions that have circular shape.
  - The derivative `dy/dx` of a polar function is calculated by:
    - `dy/dθ` can be obtained from _`y = rcosθ`_, which is ![$r \cos{\theta}+ \frac{dy}{d \theta} \sin{\theta}$](https://render.githubusercontent.com/render/math?math=%24r+%5Ccos%7B%5Ctheta%7D%2B+%5Cfrac%7Bdy%7D%7Bd+%5Ctheta%7D+%5Csin%7B%5Ctheta%7D%24).
    - `dx/dθ` can be obtained from _`x = rsinθ`_, which is ![$-r \sin{\theta}+ \frac{dy}{d \theta} \cos{\theta}$](https://render.githubusercontent.com/render/math?math=%24-r+%5Csin%7B%5Ctheta%7D%2B+%5Cfrac%7Bdy%7D%7Bd+%5Ctheta%7D+%5Ccos%7B%5Ctheta%7D%24).
    - Then, ![$\frac{dy}{dx} = \frac{\frac{dy}{d \theta}}{\frac{dx}{d \theta}}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bdy%7D%7Bdx%7D+%3D+%5Cfrac%7B%5Cfrac%7Bdy%7D%7Bd+%5Ctheta%7D%7D%7B%5Cfrac%7Bdx%7D%7Bd+%5Ctheta%7D%7D%24)
- Partial Derivatives
  - When a function has more than one independent variable, the partial derivative can be used to represent how much the dependent variable changes when one of its independent variables changes while keeping the other independent variable constant.
  - For `f(x, y)` it can have two derivatives which are `∂f/∂x` and `∂f/∂y`.
  - Function with multiple independent variable has a multi-demensional graph, parial derivative only looks at the rate of change between one independent variable and the dependent variable in one plane. All other independent variable will be kept in the result and the derivative function will have a reduced demension(by 1).

#### Rules

- Derivative of a Constant Function ![$\frac{d}{dx}(c)=0$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D(c%29%3D0%24)
- The Power Rule - ![$\frac{d}{dx}(x^n)=nx^{n-1}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D(x%5En%29%3Dnx%5E%7Bn-1%7D%24)
- The Constant Multiple Rule - If _c_ is a constant and _f_ is a differentiable function, then ![$\frac{d}{dx}[cf(x)]=c \frac{d}{dx}f(x)$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%5Bcf(x%29%5D%3Dc%20%5Cfrac%7Bd%7D%7Bdx%7Df(x%29%24)
- The Sum Rule - If _f_ and _g_ are both differentiable, then ![$\frac{d}{dx}[f(x)+g(x)]= \frac{d}{dx}f(x)+\frac{d}{dx}g(x)$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%5Bf(x%29%2Bg(x%29%5D%3D%20%5Cfrac%7Bd%7D%7Bdx%7Df(x%29%2B%5Cfrac%7Bd%7D%7Bdx%7Dg(x%29%24)
- The Difference Rule - If _f_ and _g_ are both differentiable, then ![$\frac{d}{dx}[f(x)-g(x)]= \frac{d}{dx}f(x)-\frac{d}{dx}g(x)$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%5Bf(x%29-g(x%29%5D%3D%20%5Cfrac%7Bd%7D%7Bdx%7Df(x%29-%5Cfrac%7Bd%7D%7Bdx%7Dg(x%29%24)
- Derivative of the Natural Exponential Function - ![$\frac{d}{dx}(e^x)=e^x$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D(e%5Ex%29%3De%5Ex%24)
- The Product Rule - If _f_ and _g_ are both differentiable, then ![$\frac{d}{dx}[f(x)g(x)]=f(x) \frac{d}{dx}[g(x)]+g(x) \frac{d}{dx}[f(x)]$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%5Bf(x%29g(x%29%5D%3Df(x%29%20%5Cfrac%7Bd%7D%7Bdx%7D%5Bg(x%29%5D%2Bg(x%29%20%5Cfrac%7Bd%7D%7Bdx%7D%5Bf(x%29%5D%24)
- The Quotient Rule - If _f_ and _g_ are differentiable, then ![$\frac{d}{dx}\left[\frac{f(x)}{g(x)}\right]=\frac{g(x) \frac{d}{dx}[f(x)]-f(x) \frac{d}{dx}[g(x)]}{[g(x)]^2}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%5Cleft%5B%5Cfrac%7Bf(x%29%7D%7Bg(x%29%7D%5Cright%5D%3D%5Cfrac%7Bg(x%29%20%5Cfrac%7Bd%7D%7Bdx%7D%5Bf(x%29%5D-f(x%29%20%5Cfrac%7Bd%7D%7Bdx%7D%5Bg(x%29%5D%7D%7B%5Bg(x%29%5D%5E2%7D%24)
- The Chain Rule - If _g_ is differentiable at _x_ and _f_ is differentiable at _g(x)_, then the composite function ![$F=f \circ g$](https://render.githubusercontent.com/render/math?math=%24F%3Df%20%5Ccirc%20g%24) defined by ![$F(x)=f(g(x))$](https://render.githubusercontent.com/render/math?math=%24F(x%29%3Df(g(x%29%29%24)is differentiable at _x_ and _F'_ is given by the product ![$F'(x)=f'(g(x%29%29 \cdot g'(x%29$](https://render.githubusercontent.com/render/math?math=%24F'(x%29%3Df'(g(x%29%29%20%5Ccdot%20g'(x%29%24) In Leibniz notation, if _y = f(u)_ and _u = g(x)_ are both differentiable functions, then ![$\frac{dy}{dx}= \frac{dy}{du} \frac{du}{dx}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bdy%7D%7Bdx%7D%3D%20%5Cfrac%7Bdy%7D%7Bdu%7D%20%5Cfrac%7Bdu%7D%7Bdx%7D%24)

#### Derivatives of Common Functions

- Derivatives of Trigonometric Functions
  - ![$\frac{d}{dx} (\sin x)=\cos x$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%20(%5Csin%20x%29%3D%5Ccos%20x%24)
  - ![$\frac{d}{dx} (\cos x)=-\sin x$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%20(%5Ccos%20x%29%3D-%5Csin%20x%24)
  - ![$\frac{d}{dx} (\tan x)=\sec^2 x$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%20(%5Ctan%20x%29%3D%5Csec%5E2%20x%24)
  - ![$\frac{d}{dx} (\csc x)=-\csc x \cot x$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%20(%5Ccsc%20x%29%3D-%5Ccsc%20x%20%5Ccot%20x%24)
  - ![$\frac{d}{dx} (\csc x)=-\csc x : \cot x$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%20(%5Ccsc%20x%29%3D-%5Ccsc%20x%20%5C%3A%20%5Ccot%20x%24)
  - ![$\frac{d}{dx} (\sec x)=\sec x : \tan x$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%20(%5Csec%20x%29%3D%5Csec%20x%20%5C%3A%20%5Ctan%20x%24)
  - ![$\frac{d}{dx} (\cot x)=-\csc^2 x$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%20(%5Ccot%20x%29%3D-%5Ccsc%5E2%20x%24)
- Derivatives of Inverse Trigonometric Functions
  - ![$\frac{d}{dx}(\sin^{-1}{x})=\frac{1}{\sqrt{1-x^2}}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D(%5Csin%5E%7B-1%7D%7Bx%7D%29%3D%5Cfrac%7B1%7D%7B%5Csqrt%7B1-x%5E2%7D%7D%24)
  - ![$\frac{d}{dx}(\cos^{-1}{x})=-\frac{1}{\sqrt{1-x^2}}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D(%5Ccos%5E%7B-1%7D%7Bx%7D%29%3D-%5Cfrac%7B1%7D%7B%5Csqrt%7B1-x%5E2%7D%7D%24)
  - ![$\frac{d}{dx}(\tan^{-1}{x})=\frac{1}{1+x^2}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D(%5Ctan%5E%7B-1%7D%7Bx%7D%29%3D%5Cfrac%7B1%7D%7B1%2Bx%5E2%7D%24)
  - ![$\frac{d}{dx}(\csc^{-1}{x})=-\frac{1}{x \sqrt{x^2-1}}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D(%5Ccsc%5E%7B-1%7D%7Bx%7D%29%3D-%5Cfrac%7B1%7D%7Bx%20%5Csqrt%7Bx%5E2-1%7D%7D%24)
  - ![$\frac{d}{dx}(\sec^{-1}{x})=\frac{1}{x \sqrt{x^2-1}}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D(%5Csec%5E%7B-1%7D%7Bx%7D%29%3D%5Cfrac%7B1%7D%7Bx%20%5Csqrt%7Bx%5E2-1%7D%7D%24)
  - ![$\frac{d}{dx}(\cot^{-1}{x})=-\frac{1}{1+x^2}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D(%5Ccot%5E%7B-1%7D%7Bx%7D%29%3D-%5Cfrac%7B1%7D%7B1%2Bx%5E2%7D%24)
- Derivative of Logarithmic Functions
  - ![$\frac{d}{dx}(\log_{b}{x})=\frac{1}{x \ln{b}}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D(%5Clog_%7Bb%7D%7Bx%7D%29%3D%5Cfrac%7B1%7D%7Bx%20%5Cln%7Bb%7D%7D%24)
  - ![$\frac{d}{dx}(\ln{x})=\frac{1}{x}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D(%5Cln%7Bx%7D%29%3D%5Cfrac%7B1%7D%7Bx%7D%24) or ![$\frac{d}{dx} \ln{|x|}=\frac{1}{x}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%7D%7Bdx%7D%20%5Cln%7B%7Cx%7C%7D%3D%5Cfrac%7B1%7D%7Bx%7D%24)
- Derivatives of Hyperbolic Functions
- Derivatives of Inverse Hyperbolic Functions

#### Theorem

- If _f_ is differentiable at _a_, then _f_ is continuous at _a_.
- The only solutions of the differential equation _dy/dt=ky_ where _k_ is a constant, are the exponential functions ![$y(t) = y(0)e^{kt}$](https://render.githubusercontent.com/render/math?math=%24y(t%29%20%3D%20y(0%29e%5E%7Bkt%7D%24)
  - _dy/dt=ky_ is called the law of natural growth if _k>0_ or the law of natural decay if _k<0_.
- The Extreme Value Theorem - If _f_ is continuous on a closed interval [_a, b_] then _f_ attains an absolute maximum value _f(c)_ and an absolute minimum value _f(d)_ at some numbers _c_ and _d_ in [_a, b_].
- Fermat’s Theorem - If _f_ has a local maximum or minimum at _c_, and if _f'(c)_
  exists, then _f'(c) = 0_.
- Rolle’s Theorem - Let _f_ be a function that satisfies the following three hypotheses, Then there is a number _c_ in (_a, b_) such that _f'(c)=0_:
  1. _f_ is continuous on the closed interval [_a, b_].
  2. _f_ is differentiable on the open interval (_a, b_).
  3. _f(a) = f(b)_
- The Mean Value Theorem - Let _f_ be a function that satisfies the following hypotheses, Then there is a number _c_ in (_a, b_) such that ![$f'(c) = \frac{f(b)-f(a)}{b-a}$](https://render.githubusercontent.com/render/math?math=%24f'(c%29%20%3D%20%5Cfrac%7Bf(b%29-f(a%29%7D%7Bb-a%7D%24) or, equivalently, ![$f(b)-f(a)=f'(c)(b-a)$](https://render.githubusercontent.com/render/math?math=%24f(b%29-f(a%29%3Df'(c%29(b-a%29%24) (compare to the Rolle’s Theorem the horizontal tangent line is changed to a tangent line with slope as _f'(c)_)
  1. _f_ is continuous on the closed interval [_a, b_].
  2. _f_ is differentiable on the open interval (_a, b_).
- If _f'(x)=0_ for all _x_ in an interval (_a, b_), then _f_ is constant on (_a, b_).
  - If _f'(x)-g'(x)_ for all _x_ in an interval (_a, b_), then _f - g_ is constant on (_a, b_); that is, _f(x)=g(x)+c_ where _c_ is a constant.
- If _F_ is an antiderivative of _f_ on an interval _I_, then the most general
  antiderivative of _f_ on _I_ is _F(x) + C_ where _C_ is an arbitrary constant.

#### Solving Methods for Related Problem

- Chain rule applys to all variable except the one that is at the denomination in the Leibniz notation.
  - If `dx` is the variable that is at the denomination in the Leibniz notation and `y` is the variable that will be applied by chain rule. When the relationship between `y` and `x` is unknown, use `y'` or `dy/dx` to represent the derivative of `y` in respect to `x`.
- Implicit differentiation. This consists of differentiating both sides of the equation with respect to _x_ and then solving the resulting equation for _y'_.
  - The result should be an expression which is consisted of _x_ and _y_.
- Logarithmic differentiation - The calculation of derivatives of complicated functions involving products, quotients, or powers can often be simplified by taking logarithms. The method used in the following example is called logarithmic differentiation.
- linear approximation - or tangent line approximation of _f_ at _a_ uses the tangent line of the function at _a_ to replace the original funtion, then make prediction about values that is close to _a_. As a result we have the linear approximation _L(x)_ equals to ![$f(a)+f'(a)(x-a)$](https://render.githubusercontent.com/render/math?math=%24f(a%29%2Bf'(a%29(x-a%29%24).
- The Closed interval Method - To find the absolute maximum and minimum values of a continuous function _f_ on a closed interval [_a, b_]:
  1. Find the values of all critical numbers of _f_ in (_a, b_).
  2. Find the values of the endpoints of the interval.
  3. The largest of the values from Steps 1 and 2 is the absolute maximum value; the smallest of these values is the absolute minimum value.
- Increasing/Decreasing Test
  - If _f'(x)>0_ on an interval, then _f_ is increasing on that interval.
  - If _f'(x)<0_ on an interval, then _f_ is decreasing on that interval.
- The First Derivative Test - Suppose that _c_ is a critical number of a continuous function _f_.
  - If _f'_ changes from positive to negative at _c_, then _f_ has a local maximum at _c_.
  - If _f'_ changes from negative to positive at _c_, then _f_ has a local minimum at _c_.
  - If _f'_ is positive to the left and right of _c_, or negative to the left and right of _c_, then _f_ has no local maximum or minimum at _c_.
  - If ![$f'(x) > 0$](https://render.githubusercontent.com/render/math?math=%24f'(x%29%20%3E%200%24) for all _`x < c`_ and ![$f'(x) < 0$](https://render.githubusercontent.com/render/math?math=%24f'(x%29%20%3C%200%24) for all _`x > c`_, then _f(c)_ is the absolute maximum value of _f_.
  - If ![$f'(x) < 0$](https://render.githubusercontent.com/render/math?math=%24f'(x%29%20%3C%200%24) for all _`x < c`_ and ![$f'(x) > 0$](https://render.githubusercontent.com/render/math?math=%24f'(x%29%20%3E%200%24) for all _`x > c`_, then _f(c)_ is the absolute minimum value of _f_.
- Concavity Test
  - If _f''(x)>0_ for all _x_ in _I_, then the graph of _f_ is concave upward on _I_.
  - If _f''(x)<0_ for all _x_ in _I_, then the graph of _f_ is concave downward on _I_.
- The Second Derivative Test - Suppose _f''_ is continuous near _c_.
  - If _f'(c)=0_ and _f''(c)>0_, then _f_ has a local minimum at _c_.
  - If _f'(c)=0_ and _f''(c)<0_, then _f_ has a local maximum at _c_.
- The Newton's method can be used to find the root(solution) of a high order function.
  - Pick a random value ![$x_1$](https://render.githubusercontent.com/render/math?math=%24x_1%24), then calculate `x - f(x)/f'(x)`, then treat the result ![$x_2$](https://render.githubusercontent.com/render/math?math=%24x_2%24) as ![$x_1$](https://render.githubusercontent.com/render/math?math=%24x_1%24) and repeat the calculation, repeat the process then the result value will be closer and closer to the root.
  - When the ![$x_n$](https://render.githubusercontent.com/render/math?math=%24x_n%24) is the root value the new result will not change since ![$f(x_n) = 0$](https://render.githubusercontent.com/render/math?math=%24f%28x_n%29+%3D+0%24) in this case.
  - This method uses the fact that the intersection between the slope of a random point and x-axis is close to the root.
  - It works no matter the starting point is at left side or right side of the root.
  - For a function with multiple roots, `x`s from differect section should be attept for each root.
  - Sometimes a wrong point may be picked when it is the (local) minimum/maximum point that makes `f'(x) = 0`.
- Common Polar Graphs - a flower shape with leaves growing from the origin.
  - `r = a sin(kθ)`
    - When `k` is odd, `k` equals to the number of leaves. and the leaf overlap with y-axis and point upward with `k = 1`, and the one of the leaves overlap with y-axis and points downward when `k = 3`, when `k = 5` the leaf points upward and so on.
    - When `k` is even, it has `2k` number of leaves and they spread evenly in all direction with no leaves overlap with all axis in four direction.
  - `r = a cos(kθ)`
    - there is always one leaf on the positive direction of the x-axis.
    - When `k` is odd, `k` equals to the number of leaves. There is alway one leaf on the positive direction of the x-axis, and all other leaves spread evenly. No leaves overlap with the other 3 direction on the axis.
    - When `k` is even, it has `2k` number of leaves and they spread evenly in all direction with four leaves always overlap with all axis in four direction.
  - `r = 1 + k sinθ`
    - When `k = 0` it is a circle
    - When `k > 0` it is a heart shape growing upwards as k increse and have an empty hole inside when `k > 1`
    - When `k < 0` it is a heart shape growing downward as k decrease and have an empty hole inside when `k > -1`
- When solving partial derivative just treat all other variable as constant and use the same methods and rules for a regular derivative problem.
- Function with multiple independent variables can still be used to solve for a regular derivative for a certain independent variable, in this case other independent variable can not be treated as a constant and all rules for variables like chain rules should apply.

## Integral

#### Definition

- The area _A_ of the region _S_ that lies under the graph of the continuous function _f_ is the limit of the sum of the areas of approximating rectangles:
  - ![$A=\lim_{n \to \infty} R_n= \lim_{n \to \infty}[f(x_1) \Delta x+f(x_2) \Delta x+ \ldots +f(x_n) \Delta x]$](https://render.githubusercontent.com/render/math?math=%24A%3D%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20R_n%3D%20%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%5Bf(x_1%29%20%5CDelta%20x%2Bf(x_2%29%20%5CDelta%20x%2B%20%5Cldots%20%2Bf(x_n%29%20%5CDelta%20x%5D%24)
- Definition of a Definite Integral - If _f_ is a function defined for ![$a \leqslant x \leqslant b$](https://render.githubusercontent.com/render/math?math=%24a%20%5Cleqslant%20x%20%5Cleqslant%20b%24), we divide the interval [_a, b_] into _n_ subintervals of equal width ![$\Delta x = (b-a)/n$](https://render.githubusercontent.com/render/math?math=%24%5CDelta%20x%20%3D%20(b-a%29%2Fn%24). We let ![$x_0(=a),x_1,x_2, \ldots ,x_n(=b)$](https://render.githubusercontent.com/render/math?math=%24x_0(%3Da%29%2Cx_1%2Cx_2%2C%20%5Cldots%20%2Cx_n(%3Db%29%24) be the endpoints of these subintervals and we let ![$x^*_1,x^*_2, \ldots ,x^*_n$](https://render.githubusercontent.com/render/math?math=%24x%5E*_1%2Cx%5E*_2%2C%20%5Cldots%20%2Cx%5E*_n%24) be any sample points in these subintervals, so ![$x^*_i$](https://render.githubusercontent.com/render/math?math=%24x%5E*_i%24) lies in the _ith_ subinterval ![$[x_{i-1},x_i]$](https://render.githubusercontent.com/render/math?math=%24%5Bx_%7Bi-1%7D%2Cx_i%5D%24). Then the definite integral of _f_ from _a_ to _b_ is ![$\int^b_a f(x) dx=\lim_{n \to \infty} \sum_{i=1}^n f(x^*_i) \Delta x$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_a%20f(x%29%20dx%3D%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20%5Csum_%7Bi%3D1%7D%5En%20f(x%5E*_i%29%20%5CDelta%20x%24) provided that this limit exists and gives the same value for all possible choices of sample points. If it does exist, we say that f is integrable on [_a, b_].
  - sample point usually is the right endpoint of the _ith_ subinterval
  - sample point can also be the mid point.
- Indefinite Integrals - ![$\int f(x) ; dx = F(x)$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20f(x%29%20%5C%3B%20dx%20%3D%20F(x%29%24) means _F'(x)=f(x)_
  - Indefinite Integrals represents a function, Definite Integrals represents a value.
- Definition of Volume - Let _S_ be a solid that lies between _x = a_, _x = b_. If the cross-sectional area of _S_ in the plane ![$P_x$](https://render.githubusercontent.com/render/math?math=%24P_x%24), through _x_ and perpendicular to the x-axis, is _A(x)_, where _A_ is a continuous function, then the volume of S is ![$V = \lim_{n \to \infty} \sum^n_{i=1} A(x^*_i) \Delta x = \int^b_a A(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24V%20%3D%20%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20%5Csum%5En_%7Bi%3D1%7D%20A(x%5E*_i%29%20%5CDelta%20x%20%3D%20%5Cint%5Eb_a%20A(x%29%20%5C%3B%20dx%24)
- Formula for integration by parts is as ![$\int u ; dv = uv - \int v ; du$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20u%20%5C%3B%20dv%20%3D%20uv%20-%20%5Cint%20v%20%5C%3B%20du%24)
- integration by parts also works for definite integral. ![$$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_a%20f(x%29g'(x%29%20%5C%3B%20dx%3Df(x%29g(x%29%5D%5Eb_a%20-%20%5Cint%5Eb_a%20g(x%29f'(x%29%20%5C%3B%20dx%24)
- Definition of an Improper Integral of Type 1(infinite boundary for infinite integrals)
  - If ![$\int^t_a f(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Et_a%20f(x%29%20%5C%3B%20dx%24) exists for every number ![$t \geqslant a$](https://render.githubusercontent.com/render/math?math=%24t%20%5Cgeqslant%20a%24), ![$\int^{\infty}_{a} f(x) ; dx=\lim_{t \to \infty} \int^t_a f(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5E%7B%5Cinfty%7D_%7Ba%7D%20f(x%29%20%5C%3B%20dx%3D%5Clim_%7Bt%20%5Cto%20%5Cinfty%7D%20%5Cint%5Et_a%20f(x%29%20%5C%3B%20dx%24) provided this limit exists (as a finite number).
  - If ![$\int^b_t f(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_t%20f(x%29%20%5C%3B%20dx%24) exists for every number ![$t \leqslant b$](https://render.githubusercontent.com/render/math?math=%24t%20%5Cleqslant%20b%24), ![$\int^{b}_{- \infty} f(x) ; dx=\lim_{t \to - \infty} \int^b_t f(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5E%7Bb%7D_%7B-%20%5Cinfty%7D%20f(x%29%20%5C%3B%20dx%3D%5Clim_%7Bt%20%5Cto%20-%20%5Cinfty%7D%20%5Cint%5Eb_t%20f(x%29%20%5C%3B%20dx%24) provided this limit exists (as a finite number).
  - The improper integrals are called convergent if the corresponding limit exists and divergent if the limit does not exist. If both ![$\int^{\infty}_{a}f(x)$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5E%7B%5Cinfty%7D_%7Ba%7Df(x%29%24) and ![$\int^{a}_{- \infty}f(x)$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5E%7Ba%7D_%7B-%20%5Cinfty%7Df(x%29%24) are convergent, then we define ![$\int^{\infty}_{- \infty}f(x) ; dx=\int^{a}_{- \infty}f(x) ; dx+ \int^{\infty}_{a}f(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5E%7B%5Cinfty%7D_%7B-%20%5Cinfty%7Df(x%29%20%5C%3B%20dx%3D%5Cint%5E%7Ba%7D_%7B-%20%5Cinfty%7Df(x%29%20%5C%3B%20dx%2B%20%5Cint%5E%7B%5Cinfty%7D_%7Ba%7Df(x%29%20%5C%3B%20dx%24) where any real number _a_ can be used.
- Definition of an Improper Integral of Type 2(infinite boundary for definite integrals)
  - If _f_ is continuous on [_a, b_) and is discontinuous at _b_, then ![$\int^b_a f(x) ; dx = \lim_{t \to b^-} \int^t_a f(x) ;dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_a%20f(x%29%20%5C%3B%20dx%20%3D%20%5Clim_%7Bt%20%5Cto%20b%5E-%7D%20%5Cint%5Et_a%20f(x%29%20%5C%3Bdx%24) if this limit exists (as a finite number).
  - If _f_ is continuous on (_a, b_] and is discontinuous at _b_, then ![$\int^b_a f(x) ; dx = \lim_{t \to a^+} \int^b_t f(x) ;dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_a%20f(x%29%20%5C%3B%20dx%20%3D%20%5Clim_%7Bt%20%5Cto%20a%5E%2B%7D%20%5Cint%5Eb_t%20f(x%29%20%5C%3Bdx%24) if this limit exists (as a finite number).
  - The improper integral is called convergent if the corresponding limit exists and divergent if the limit does not exist.
  - If _f_ has a discontinuity at _c_, where _a < c < b_ and both integrals are convergent, then we define ![$\int^b_a f(x) ; dx=\int^c_a f(x) ; dx + \int^b_c f(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_a%20f(x%29%20%5C%3B%20dx%3D%5Cint%5Ec_a%20f(x%29%20%5C%3B%20dx%20%2B%20%5Cint%5Eb_c%20f(x%29%20%5C%3B%20dx%24)

#### Theorem

- If _f_ is continuous on [_a, b_], or if _f_ has only a finite number of jump discontinuities, then f is integrable on [_a, b_]; that is, the definite integral ![$\int^b_a f(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_a%20f(x%29%20%5C%3B%20dx%24) exists.
- If _f_ is integrable on [_a, b_], then ![$\int^b_a f(x) ; dx=\lim_{n \to \infty} \sum_{i=1}^n f(x_i) \Delta x$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_a%20f(x%29%20%5C%3B%20dx%3D%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20%5Csum_%7Bi%3D1%7D%5En%20f(x_i%29%20%5CDelta%20x%24) where ![$\Delta x= \frac{b-a}{n}$](https://render.githubusercontent.com/render/math?math=%24%5CDelta%20x%3D%20%5Cfrac%7Bb-a%7D%7Bn%7D%24) and ![$x_i=a+i \Delta x$](https://render.githubusercontent.com/render/math?math=%24x_i%3Da%2Bi%20%5CDelta%20x%24)
- the Fundamental theorem of calculus
  - If _f_ is continuous on [_a, b_], then the function _g_ defined by ![$g(x)= \int^x_a f(t) ; dt ; ; ; a \leqslant x \leqslant b$](https://render.githubusercontent.com/render/math?math=%24g(x%29%3D%20%5Cint%5Ex_a%20f(t%29%20%5C%3B%20dt%20%5C%3B%20%5C%3B%20%5C%3B%20a%20%5Cleqslant%20x%20%5Cleqslant%20b%24) is continuous on [_a, b_] and differentiable on (_a, b_), and ![$g'(x)=f(x)$](https://render.githubusercontent.com/render/math?math=%24g'(x%29%3Df(x%29%24).
  - If _f_ is continuous on [_a, b_], then ![$\int^b_a f(x) ; dx = F(b) - F(a)$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_a%20f(x%29%20%5C%3B%20dx%20%3D%20F(b%29%20-%20F(a%29%24) where _F_ is any antiderivative of _f_, that is, a function such that _F'=f_.
- Net Change Theorem - The integral of a rate of change is the net change: ![$\int^b_a F'(x) ; dx=F(b)-F(a)$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_a%20F'(x%29%20%5C%3B%20dx%3DF(b%29-F(a%29%24)
- The Mean Value Theorem for Integrals - If _f_ is continuous on [_a, b_], then there exists a number _c_ in [_a, b_] such that ![$f(c)=f_{avg}=\frac{1}{b-a} \int^b_a f(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24f(c%29%3Df_%7Bavg%7D%3D%5Cfrac%7B1%7D%7Bb-a%7D%20%5Cint%5Eb_a%20f(x%29%20%5C%3B%20dx%24) that is, ![$\int^b_a f(x) ; dx = f(c)(b-a)$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_a%20f(x%29%20%5C%3B%20dx%20%3D%20f(c%29(b-a%29%24)
- Comparison Theorem - Suppose that _f_ and _g_ are continuous functions with ![$f(x) \geqslant g(x) \geqslant 0$](https://render.githubusercontent.com/render/math?math=%24f(x%29%20%5Cgeqslant%20g(x%29%20%5Cgeqslant%200%24) for ![$x \geqslant a$](https://render.githubusercontent.com/render/math?math=%24x%20%5Cgeqslant%20a%24)
  - If ![$\int^{\infty}_a f(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5E%7B%5Cinfty%7D_a%20f(x%29%20%5C%3B%20dx%24) is convergent, then ![$\int^{\infty}_a g(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5E%7B%5Cinfty%7D_a%20g(x%29%20%5C%3B%20dx%24) is convergent.
  - If ![$\int^{\infty}_a g(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5E%7B%5Cinfty%7D_a%20g(x%29%20%5C%3B%20dx%24) is divergent, then ![$\int^{\infty}_a f(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5E%7B%5Cinfty%7D_a%20f(x%29%20%5C%3B%20dx%24) is divergent.

#### Properties

- Properties of the Definite Integral
  - ![$\int^a_b f(x) ; dx=- \int^b_a f(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Ea_b%20f(x%29%20%5C%3B%20dx%3D-%20%5Cint%5Eb_a%20f(x%29%20%5C%3B%20dx%24)
  - ![$\int^a_a f(x) ; dx=0$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Ea_a%20f(x%29%20%5C%3B%20dx%3D0%24)
  - ![$\int^b_a c ; dx=c(b-a)$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_a%20c%20%5C%3B%20dx%3Dc(b-a%29%24) where _c_ is any constant.
  - ![$\int^b_a cf(x) ; dx=c \int^b_a f(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_a%20cf(x%29%20%5C%3B%20dx%3Dc%20%5Cint%5Eb_a%20f(x%29%20%5C%3B%20dx%24) where _c_ is any constant.
  - ![$\int^b_a [f(x)+g(x)] ; dx=\int^b_a f(x) ; dx + \int^b_a g(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_a%20%5Bf(x%29%2Bg(x%29%5D%20%5C%3B%20dx%3D%5Cint%5Eb_a%20f(x%29%20%5C%3B%20dx%20%2B%20%5Cint%5Eb_a%20g(x%29%20%5C%3B%20dx%24)
  - ![$\int^b_a [f(x)-g(x)] ; dx=\int^b_a f(x) ; dx - \int^b_a g(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_a%20%5Bf(x%29-g(x%29%5D%20%5C%3B%20dx%3D%5Cint%5Eb_a%20f(x%29%20%5C%3B%20dx%20-%20%5Cint%5Eb_a%20g(x%29%20%5C%3B%20dx%24)
  - ![$\int^c_a f(x) ; dx + \int^b_c f(x) ; dx = \int^b_a f(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Ec_a%20f(x%29%20%5C%3B%20dx%20%2B%20%5Cint%5Eb_c%20f(x%29%20%5C%3B%20dx%20%3D%20%5Cint%5Eb_a%20f(x%29%20%5C%3B%20dx%24)
- Comparison Properties of the Integral
  - If ![$f(x) \geqslant 0$](https://render.githubusercontent.com/render/math?math=%24f(x%29%20%5Cgeqslant%200%24) for ![$a \leqslant x \leqslant b$](https://render.githubusercontent.com/render/math?math=%24a%20%5Cleqslant%20x%20%5Cleqslant%20b%24), then ![$\int^b_a f(x) ; dx \geqslant 0$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_a%20f(x%29%20%5C%3B%20dx%20%5Cgeqslant%200%24).
  - If ![$f(x) \geqslant g(x)$](https://render.githubusercontent.com/render/math?math=%24f(x%29%20%5Cgeqslant%20g(x%29%24) for ![$a \leqslant x \leqslant b$](https://render.githubusercontent.com/render/math?math=%24a%20%5Cleqslant%20x%20%5Cleqslant%20b%24), then ![$\int^b_a f(x) ; dx \geqslant \int^b_a g(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_a%20f(x%29%20%5C%3B%20dx%20%5Cgeqslant%20%5Cint%5Eb_a%20g(x%29%20%5C%3B%20dx%24).
  - If ![$m \leqslant f(x) \leqslant M$](https://render.githubusercontent.com/render/math?math=%24m%20%5Cleqslant%20f(x%29%20%5Cleqslant%20M%24) for ![$a \leqslant x \leqslant b$](https://render.githubusercontent.com/render/math?math=%24a%20%5Cleqslant%20x%20%5Cleqslant%20b%24), then ![$m(b-a) \leqslant \int^b_a f(x) ; dx \leqslant M(b-a)$](https://render.githubusercontent.com/render/math?math=%24m(b-a%29%20%5Cleqslant%20%5Cint%5Eb_a%20f(x%29%20%5C%3B%20dx%20%5Cleqslant%20M(b-a%29%24)
- Properties of the Indefinite Integral
  - ![$\int cf(x) ; dx=c \int f(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20cf(x%29%20%5C%3B%20dx%3Dc%20%5Cint%20f(x%29%20%5C%3B%20dx%24)
  - ![$\int k ; dx=kx+C$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20k%20%5C%3B%20dx%3Dkx%2BC%24)
  - ![$\int [f(x)+g(x)] ; dx=\int f(x); dx+ \int g(x); dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20%5Bf(x%29%2Bg(x%29%5D%20%5C%3B%20dx%3D%5Cint%20f(x%29%5C%3B%20dx%2B%20%5Cint%20g(x%29%5C%3B%20dx%24)
  - ![$\int x^n ; dx= \frac{x^{n+1}}{n+1}+C ; (n \neq -1)$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20x%5En%20%5C%3B%20dx%3D%20%5Cfrac%7Bx%5E%7Bn%2B1%7D%7D%7Bn%2B1%7D%2BC%20%5C%3B%20(n%20%5Cneq%20-1%29%24)
  - ![$\int \frac{1}{x} ; dx=\ln{|x|}+C$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20%5Cfrac%7B1%7D%7Bx%7D%20%5C%3B%20dx%3D%5Cln%7B%7Cx%7C%7D%2BC%24)
  - ![$\int e^x ; dx = e^x +C](https://render.githubusercontent.com/render/math?math=%24%5Cint%20e%5Ex%20%5C%3B%20dx%20%3D%20e%5Ex%20%2BC)
  - ![$\int b^x ; dx = \frac{b^x}{\ln b} +C$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20b%5Ex%20%5C%3B%20dx%20%3D%20%5Cfrac%7Bb%5Ex%7D%7B%5Cln%20b%7D%20%2BC%24)
  - ![$\int \sin x ; dx= - \cos x +C$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20%5Csin%20x%20%5C%3B%20dx%3D%20-%20%5Ccos%20x%20%2BC%24)
  - ![$\int \cos x ; dx= \sin x +C$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20%5Ccos%20x%20%5C%3B%20dx%3D%20%5Csin%20x%20%2BC%24)
  - ![$\int \sex^2 x ; dx= \tan x +C$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20%5Csex%5E2%20x%20%5C%3B%20dx%3D%20%5Ctan%20x%20%2BC%24)
  - ![$\int \csc^2 x ; dx= - \cot x +C$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20%5Ccsc%5E2%20x%20%5C%3B%20dx%3D%20-%20%5Ccot%20x%20%2BC%24)
  - ![$\int \cec x ; \tan x ; dx= \sec x +C$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20%5Ccec%20x%20%5C%3B%20%5Ctan%20x%20%5C%3B%20dx%3D%20%5Csec%20x%20%2BC%24)
  - ![$\int \csc x ; \cot x ; dx=- \csc x +C$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20%5Ccsc%20x%20%5C%3B%20%5Ccot%20x%20%5C%3B%20dx%3D-%20%5Ccsc%20x%20%2BC%24)
  - ![$\int \frac{1}{x^2+1} dx=\tan^{-1} x+C$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20%5Cfrac%7B1%7D%7Bx%5E2%2B1%7D%20dx%3D%5Ctan%5E%7B-1%7D%20x%2BC%24)
  - ![$\int \frac{1}{\sqrt{1-x^2}} dx=\sin^{-1} x+C$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20%5Cfrac%7B1%7D%7B%5Csqrt%7B1-x%5E2%7D%7D%20dx%3D%5Csin%5E%7B-1%7D%20x%2BC%24)
  - ![$\int \sinh x ; dx=\cosh x +C$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20%5Csinh%20x%20%5C%3B%20dx%3D%5Ccosh%20x%20%2BC%24)
  - ![$\int \cosh x ; dx=\sinh x +C$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20%5Ccosh%20x%20%5C%3B%20dx%3D%5Csinh%20x%20%2BC%24)
  - ![$\int \tan x ; dx=\ln ; |\sec x| +C$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20%5Ctan%20x%20%5C%3B%20dx%3D%5Cln%20%5C%3B%20%7C%5Csec%20x%7C%20%2BC%24)
  - ![$\int \cot x ; dx=\ln ; |\sin x| +C$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20%5Ccot%20x%20%5C%3B%20dx%3D%5Cln%20%5C%3B%20%7C%5Csin%20x%7C%20%2BC%24)
  - ![$\int \frac{1}{x^2+a^2} ; dx=\frac{1}{a} \tan^{-1} \left(\frac{x}{a}\right)+C$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20%5Cfrac%7B1%7D%7Bx%5E2%2Ba%5E2%7D%20%5C%3B%20dx%3D%5Cfrac%7B1%7D%7Ba%7D%20%5Ctan%5E%7B-1%7D%20%5Cleft(%5Cfrac%7Bx%7D%7Ba%7D%5Cright%29%2BC%24)
  - ![$\int \frac{1}{\sqrt{a^2-x^2}} ; dx= \sin^{-1} \left(\frac{x}{a}\right)+C$](https://render.githubusercontent.com/render/math?math=%24%5Cint%20%5Cfrac%7B1%7D%7B%5Csqrt%7Ba%5E2-x%5E2%7D%7D%20%5C%3B%20dx%3D%20%5Csin%5E%7B-1%7D%20%5Cleft(%5Cfrac%7Bx%7D%7Ba%7D%5Cright%29%2BC%24), _a > 0_
- The Substitution Rule If _u=g(s)_ is a differentiable function whose range is an interval _I_ and _f_ is continuous on _I_, then ![$f(g(x))g'(x)dx=\int f(u) ; du$](https://render.githubusercontent.com/render/math?math=%24f(g(x%29%29g'(x%29dx%3D%5Cint%20f(u%29%20%5C%3B%20du%24)
- The Substitution Rule for Definite Integrals - If _g'_ is continuous on [_a, b_] and _f_ is continuous on the range of _u = g(x)_, then ![$\int^b_a f(g(x))g'(x)dx=\int^{g(b)}_{g(a)}f(u) ; du$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_a%20f(g(x%29%29g'(x%29dx%3D%5Cint%5E%7Bg(b%29%7D_%7Bg(a%29%7Df(u%29%20%5C%3B%20du%24)
- Integrals of Symmetric Functions Suppose _f_ is continuous on [_-a, a_].
  - If f is even [_f(-x) = f(x)_], then ![$\int^a_{-a} f(x) ; dx=2 \int^a_0 f(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Ea_%7B-a%7D%20f(x%29%20%5C%3B%20dx%3D2%20%5Cint%5Ea_0%20f(x%29%20%5C%3B%20dx%24)
  - If f is odd [_f(-x) = -f(x)_], ![$\int^a_{-a} f(x) ; dx=0$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Ea_%7B-a%7D%20f(x%29%20%5C%3B%20dx%3D0%24)
- Midpoint rule - ![$\int^b_a f(x) ; dx \approx M_n = \Delta x [f(\overline{x}_1)+f(\overline{x}_2)+ \cdots +f(\overline{x}_n)]$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_a%20f(x%29%20%5C%3B%20dx%20%5Capprox%20M_n%20%3D%20%5CDelta%20x%20%5Bf(%5Coverline%7Bx%7D_1%29%2Bf(%5Coverline%7Bx%7D_2%29%2B%20%5Ccdots%20%2Bf(%5Coverline%7Bx%7D_n%29%5D%24) where ![$\Delta x= \frac{b-a}{n}$](https://render.githubusercontent.com/render/math?math=%24%5CDelta%20x%3D%20%5Cfrac%7Bb-a%7D%7Bn%7D%24) and ![$\overline{x}_i = \frac{1}{2}(x_{i-1}+x_i)=$](https://render.githubusercontent.com/render/math?math=%24%5Coverline%7Bx%7D_i%20%3D%20%5Cfrac%7B1%7D%7B2%7D(x_%7Bi-1%7D%2Bx_i%29%3D%24) midpoint of ![$[x_{i-1},x_i]$](https://render.githubusercontent.com/render/math?math=%24%5Bx_%7Bi-1%7D%2Cx_i%5D%24)
- Trapezoidal Rule - ![$\int^b_a f(x) ; dx \approx T_n = \frac{\Delta x}{2}[f(x_0)+2f(x_1)+2f(x_2)+ \cdots +2f(x_{n-1})+2f(x_n)]$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_a%20f(x%29%20%5C%3B%20dx%20%5Capprox%20T_n%20%3D%20%5Cfrac%7B%5CDelta%20x%7D%7B2%7D%5Bf(x_0%29%2B2f(x_1%29%2B2f(x_2%29%2B%20%5Ccdots%20%2B2f(x_%7Bn-1%7D%29%2B2f(x_n%29%5D%24) where ![$\Delta x= (b-a)/n$](https://render.githubusercontent.com/render/math?math=%24%5CDelta%20x%3D%20(b-a%29%2Fn%24) and ![$x_i = a + i \Delta x](https://render.githubusercontent.com/render/math?math=%24x_i%20%3D%20a%20%2B%20i%20%5CDelta%20x)
  - It treats the area as the sum of many trapezoidals.
- Simpson’s Rule - ![$\int^b_a f(x) ; dx \approx S_n = \frac{\Delta x}{3}[f(x_0)+4f(x_1)+2f(x_2)+4f(x_3)+ \cdots +2f(x_{n-2})+4f(x_{n-1})+f(n)]$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5Eb_a%20f(x%29%20%5C%3B%20dx%20%5Capprox%20S_n%20%3D%20%5Cfrac%7B%5CDelta%20x%7D%7B3%7D%5Bf(x_0%29%2B4f(x_1%29%2B2f(x_2%29%2B4f(x_3%29%2B%20%5Ccdots%20%2B2f(x_%7Bn-2%7D%29%2B4f(x_%7Bn-1%7D%29%2Bf(n%29%5D%24) where n is even and ![$\Delta x= (b-a)/n$](https://render.githubusercontent.com/render/math?math=%24%5CDelta%20x%3D%20(b-a%29%2Fn%24)
- If K is a value that ![$\left|f''(x) \right| \leqslant K$](https://render.githubusercontent.com/render/math?math=%24%5Cleft%7Cf''(x%29%20%5Cright%7C%20%5Cleqslant%20K%24) for ![$a \leqslant x \leqslant b$](https://render.githubusercontent.com/render/math?math=%24a%20%5Cleqslant%20x%20%5Cleqslant%20b%24)
  - the errors in the Trapezoidal Rules is ![$|E_T| \leqslant \frac{K(b-a)^3}{12n^2}$](https://render.githubusercontent.com/render/math?math=%24%7CE_T%7C%20%5Cleqslant%20%5Cfrac%7BK(b-a%29%5E3%7D%7B12n%5E2%7D%24)
  - the errors in the Midpoint Rules is ![$|E_M| \leqslant \frac{K(b-a)^3}{24n^2}$](https://render.githubusercontent.com/render/math?math=%24%7CE_M%7C%20%5Cleqslant%20%5Cfrac%7BK(b-a%29%5E3%7D%7B24n%5E2%7D%24)
- Error Bound for simpson’s rule - If ![$\left| f^{(4)}x \right| \leqslant K$](https://render.githubusercontent.com/render/math?math=%24%5Cleft%7C%20f%5E%7B(4%29%7Dx%20%5Cright%7C%20%5Cleqslant%20K%24) for ![$a \leqslant x \leqslant b$](https://render.githubusercontent.com/render/math?math=%24a%20%5Cleqslant%20x%20%5Cleqslant%20b%24) ![$|E_S| \leqslant \frac{K(b-a)^5}{180n^4}$](https://render.githubusercontent.com/render/math?math=%24%7CE_S%7C%20%5Cleqslant%20%5Cfrac%7BK(b-a%29%5E5%7D%7B180n%5E4%7D%24)

#### Techniques

- The area _A_ of the region bounded by the curves _y = f(x)_, _y = g(x)_, and the lines _x = a_, _x = b_, where _f_ and _g_ are continuous and ![$f(x) \geqslant g(x)$](https://render.githubusercontent.com/render/math?math=%24f(x%29%20%5Cgeqslant%20g(x%29%24) for all _x_ in [_a, b_], is ![$A = \int^b_a [f(x) - g(x)] ; dx$](https://render.githubusercontent.com/render/math?math=%24A%20%3D%20%5Cint%5Eb_a%20%5Bf(x%29%20-%20g(x%29%5D%20%5C%3B%20dx%24)
- Generally, the area between the curves _y = f(x)_, _y = g(x)_, and the lines _x = a_, _x = b_ is ![$A = \int^b_a |f(x) - g(x)| ; dx$](https://render.githubusercontent.com/render/math?math=%24A%20%3D%20%5Cint%5Eb_a%20%7Cf(x%29%20-%20g(x%29%7C%20%5C%3B%20dx%24)
- Method of cylindrical shells - The volume of a cylindrical shapes, obtained by rotating about the y-axis the region under the curve _y = f(x)_ from _a_ to _b_, is ![$V = \int^b_a 2 \pi x f(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24V%20%3D%20%5Cint%5Eb_a%202%20%5Cpi%20x%20f(x%29%20%5C%3B%20dx%24) where ![$0 \leqslant a < b$](https://render.githubusercontent.com/render/math?math=%240%20%5Cleqslant%20a%20%3C%20b%24)
  - Since the volume of a cylindrical shell is ![$V=2 \pi rh \Delta r$](https://render.githubusercontent.com/render/math?math=%24V%3D2%20%5Cpi%20rh%20%5CDelta%20r%24)
- the average value of _f_ on the interval [_a, b_] is ![$f_{avg}=\frac{1}{b-a} \int^b_a f(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24f_%7Bavg%7D%3D%5Cfrac%7B1%7D%7Bb-a%7D%20%5Cint%5Eb_a%20f(x%29%20%5C%3B%20dx%24)
- A problem can be solved by integral by parts if the function can be represented by one sub function times the differentiated function of another one.
- Chain rules can be used to solved an integral by substitute a subfunction in along with _du_ when and differential function of the sub function is found and the relationship between _du_ and _dx_ is found.
- Trigonometric Integrals 7.2 7.3 7.4 7.5
- The Arc Length Formula - If _f'_ is continuous on [_a, b_] then the length of the curve _y = f(x)_, ![a \leqslant x \leqslant b](https://render.githubusercontent.com/render/math?math=a%20%5Cleqslant%20x%20%5Cleqslant%20b), is ![$L=\int^b_a \sqrt{1+[f'(x)]^2} ; dx$](https://render.githubusercontent.com/render/math?math=%24L%3D%5Cint%5Eb_a%20%5Csqrt%7B1%2B%5Bf'(x%29%5D%5E2%7D%20%5C%3B%20dx%24) or ![$L=\int^b_a \sqrt{1+\left(\frac{dy}{dx}\right)^2} ; dx$](https://render.githubusercontent.com/render/math?math=%24L%3D%5Cint%5Eb_a%20%5Csqrt%7B1%2B%5Cleft(%5Cfrac%7Bdy%7D%7Bdx%7D%5Cright%29%5E2%7D%20%5C%3B%20dx%24) using Leibniz notation.
  - the surface area of the surface obtained by rotating the curve _y = f(x)_, ![$a \leqslant x \leqslant b$](https://render.githubusercontent.com/render/math?math=%24a%20%5Cleqslant%20x%20%5Cleqslant%20b%24), about the x-axis as ![$S=\int^b_a 2 \pi y \sqrt{1+\left(\frac{dy}{dx}\right)^2} ; dx$](https://render.githubusercontent.com/render/math?math=%24S%3D%5Cint%5Eb_a%202%20%5Cpi%20y%20%5Csqrt%7B1%2B%5Cleft(%5Cfrac%7Bdy%7D%7Bdx%7D%5Cright%29%5E2%7D%20%5C%3B%20dx%24)
    - The surface area of a cone is ![$A=\pi rl$](https://render.githubusercontent.com/render/math?math=%24A%3D%5Cpi%20rl%24), the surface area of a cone when its top is cut with side length `l` is ![$A=2 \pi rl$](https://render.githubusercontent.com/render/math?math=%24A%3D2%20%5Cpi%20rl%24)
    - when rotate about the x-axis, uses ![$S=\int^b_a 2 \pi y \sqrt{1+\left(\frac{dx}{dy}\right)^2} ; dy$](https://render.githubusercontent.com/render/math?math=%24S%3D%5Cint%5Eb_a%202%20%5Cpi%20y%20%5Csqrt%7B1%2B%5Cleft(%5Cfrac%7Bdx%7D%7Bdy%7D%5Cright%29%5E2%7D%20%5C%3B%20dy%24)
  - If _x = f(y)_, uses `dy/dx`.
- Double integral is used to calculate the area of a graph by using `dx` times `dy`. It can be expressed as ![$\int^{x_2}_{x_1} dx \int^{y_2}_{y_1} dy$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5E%7Bx_2%7D_%7Bx_1%7D+dx+%5Cint%5E%7By_2%7D_%7By_1%7D+dy%24) or ![$\int^{y_2}_{y_1} \int^{x_2}_{x_1} dx dy$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5E%7By_2%7D_%7By_1%7D+%5Cint%5E%7Bx_2%7D_%7Bx_1%7D+dx+dy%24) or ![$\int^{x_2}_{x_1} \int^{y_2}_{y_1} dy dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5E%7Bx_2%7D_%7Bx_1%7D+%5Cint%5E%7By_2%7D_%7By_1%7D+dy+dx%24).
  - The first diffrential is associated with the last integral sign, The second diffrential is associated with the first integral sign,
  - `dy` can be evaluated first and the other variable `x` can be considered as constant, then the result for integral of `dy` can be subsituted by `x` then the integral of `dx` can then be evaluated.
  - Optionally, `dx` can be evaluated first and considering `y` as constant. then subsitute `x` by expression of `y` then take the integral of `dy` and get the result.

## Differential Equation

#### Definition

- First Order Differential Equation - it is an equation that contains both the function itself and its derivates. For example, ![$\frac{dx}{dt}=x^2 t$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bdx%7D%7Bdt%7D%3Dx%5E2%20t%24) where _x = f(t)_. Then, solve for the function _f(t)_
- Second Order Differential Equation - it is an equation that contains both the function itself and its first and second derivates. For example, ![$\frac{d^2y}{dx^2}-2 \frac{dy}{dx}+8y=0$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Bd%5E2y%7D%7Bdx%5E2%7D-2%20%5Cfrac%7Bdy%7D%7Bdx%7D%2B8y%3D0%24) or it can be _y'-2y'+8y = 0_ where _y = f(x)_. Then, solve for the function _f(x)_
- The solution will have a constant C that make differential equations have infinite solutions and this is called the general solution.
- A slope field can be drawn based on general solution.
  - fill the graph with short lines that represent a slope at that point.
- Infinite solution curves can be drawn based on slope fields.
- When the constant is given or the a initial value is given, a particular solution can be found.
- Linear first order differential equation has a form as _y' + P(x)y = Q(x)_
- Non-linear first order differential equations are others in a form like _y' = f(x, y)_
- Linear second order differential equation has a form as _y'' + P(x)y' + Q(x)y = S(x)_ where _P(x)_, _Q(x)_, _S(x)_ can be either a constant or a function of x.
  - Linear second order differential equation become homogeneous when _S(x)_ is zero
  - non-homogeneous when _S(x)_ is not zero, _S(x)_ can be called the driven function.

#### Techniques

- Solving First Order Differential Equation
  - For equations like _y' = f(t)f(y)_, use Separation of Variables - place _t_ and _dt_ on one side of the equation and _y_ and _dy_ on the other side, then take the integrate both side of the function.
  - For linear first order differential equation, multiply both sides of the equation by an integrating factor ![$P(x)=e^{\int P(x) ; dx}$](https://render.githubusercontent.com/render/math?math=%24P(x%29%3De%5E%7B%5Cint%20P(x%29%20%5C%3B%20dx%7D%24)
  - For Non-linear first order differential equations use substitution method.
  - For homogeneous first order differential equations in form as _y' = F(x/y)_, substitute `v = x/y` into _F(x/y)_
  - The exact differential equations - _F(x, y(x))_ can be solved if _M(x, y)dx + N(x, y)dy = 0_ where _dF/dx = M_ and _dF/dy = N_.
  - Solving Second Order Differential Equation
    - For equations like has variables _F(x, y', y'')_ it can be reduced to first order by substituting _p = dy/dx_ and _y'' = dp/dx_.
    - Linear non-homogeneous second order differential equation, solve the homogeneous version of the equation and add the driven function to the homogeneous solution.

## Infinite Sequences and Series

#### Definition

- A sequence can be thought of as a list of numbers written in a definite order: ![$a_1,a_2,a_3,a_4, \ldots, a_n, \ldots$](https://render.githubusercontent.com/render/math?math=%24a_1%2Ca_2%2Ca_3%2Ca_4%2C%20%5Cldots%2C%20a_n%2C%20%5Cldots%24)
  - The elements can be described as the _nth_ term of the sequence.
  - The sequence can also be denoted by ![${a_n}$](https://render.githubusercontent.com/render/math?math=%24%5C%7Ba_n%5C%7D%24) or ![${a_n}^{\infty}_{n=1}$](https://render.githubusercontent.com/render/math?math=%24%5C%7Ba_n%5C%7D%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%24)
  - Some sequences can be defined by giving a formula for the nth term.
- The Fibonacci sequence ![${f_n}$](https://render.githubusercontent.com/render/math?math=%24%5C%7Bf_n%5C%7D%24) is defined recursively by the conditions ![$f_1=1 ; ;;; f_2=1 ;;;; f_n=f_{n-1}+f_{n-2} ;;; n \geqslant 3$](https://render.githubusercontent.com/render/math?math=%24f_1%3D1%20%5C%3B%20%5C%3B%5C%3B%5C%3B%20f_2%3D1%20%5C%3B%5C%3B%5C%3B%5C%3B%20f_n%3Df_%7Bn-1%7D%2Bf_%7Bn-2%7D%20%5C%3B%5C%3B%5C%3B%20n%20%5Cgeqslant%203%24)
- Intuitive Definition of Sequences' Limit - A sequence ![${a_n}$](https://render.githubusercontent.com/render/math?math=%24%5C%7Ba_n%5C%7D%24) has the limit _L_ and we write ![$\lim_{n \to \infty} a_n=L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20a_n%3DL%24)
  - If L exists we say the sequence converges (or is convergent). Otherwise, we say the sequence diverges (or is divergent).
- Precise Definition of Sequences' Limit - A sequence ![${a_n}$](https://render.githubusercontent.com/render/math?math=%24%5C%7Ba_n%5C%7D%24) has the limit _L_ and we write ![$\lim_{n \to \infty} a_n=L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20a_n%3DL%24) if for every ![$\epsilon > 0$](https://render.githubusercontent.com/render/math?math=%24%5Cepsilon%20%3E%200%24) there is a corresponding integer _N_ such that if _n > N_ then ![$|a_n-L| < \epsilon](https://render.githubusercontent.com/render/math?math=%24%7Ca_n-L%7C%20%3C%20%5Cepsilon)
- ![$\lim_{n \to \infty} a_n= \infty$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20a_n%3D%20%5Cinfty%24) means that for every positive number _M_ there is an integer _N_ such that if _n > N_ then ![$a_n > M$](https://render.githubusercontent.com/render/math?math=%24a_n%20%3E%20M%24)
- A sequence ![${a_n}$](https://render.githubusercontent.com/render/math?math=%24%5C%7Ba_n%5C%7D%24) is called increasing if ![$a_n < a_{n+1}](https://render.githubusercontent.com/render/math?math=%24a_n%20%3C%20a_%7Bn%2B1%7D)for all ![$n \geqslant 1$](https://render.githubusercontent.com/render/math?math=%24n%20%5Cgeqslant%201%24), that is, ![$a_1 < a_2 < a_3 < \cdots$](https://render.githubusercontent.com/render/math?math=%24a_1%20%3C%20a_2%20%3C%20a_3%20%3C%20%5Ccdots%24). It is called decreasing if ![$a_n > a_{n+1}](https://render.githubusercontent.com/render/math?math=%24a_n%20%3E%20a_%7Bn%2B1%7D) for all ![$n \geqslant 1$](https://render.githubusercontent.com/render/math?math=%24n%20%5Cgeqslant%201%24).
  - A sequence is monotonic if it is either increasing or decreasing.
- A sequence ![${a_n}$](https://render.githubusercontent.com/render/math?math=%24%5C%7Ba_n%5C%7D%24) is bounded above if there is a number _M_ such that ![$a_n \leqslant M$](https://render.githubusercontent.com/render/math?math=%24a_n%20%5Cleqslant%20M%24) for all ![$n \geqslant 1$](https://render.githubusercontent.com/render/math?math=%24n%20%5Cgeqslant%201%24). It is bounded below if there is a number _m_ such that ![$m \leqslant a_n$](https://render.githubusercontent.com/render/math?math=%24m%20%5Cleqslant%20a_n%24) for all ![$n \geqslant 1$](https://render.githubusercontent.com/render/math?math=%24n%20%5Cgeqslant%201%24).
  - If it is bounded above and below, then the sequence is a bounded sequence.
- In general, if we try to add the terms of an infinite sequence ![${a_n}^{\infty}_{n=1}$](https://render.githubusercontent.com/render/math?math=%24%5C%7Ba_n%5C%7D%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%24) we get an expression ![$a_1+a_2+a_3+ \cdots +a_n+ \cdots$](https://render.githubusercontent.com/render/math?math=%24a_1%2Ba_2%2Ba_3%2B%20%5Ccdots%20%2Ba_n%2B%20%5Ccdots%24) which is called an infinite series (or just a series) and is denoted, for short, by the symbol ![$\sum^{\infty}_{n=1} a_n](https://render.githubusercontent.com/render/math?math=%24%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20a_n) or ![$\sum a_n](https://render.githubusercontent.com/render/math?math=%24%5Csum%20a_n)
- Given a series ![$\sum^{\infty}_{n=1} a_n=a_1+a_2+a_3+ \cdots$](https://render.githubusercontent.com/render/math?math=%24%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20a_n%3Da_1%2Ba_2%2Ba_3%2B%20%5Ccdots%24), the partial sum of the first _n_ terms is ![$s_n = \sum^{n}_{i=1} a_i=a_1+a_2+ \cdots +a_n$](https://render.githubusercontent.com/render/math?math=%24s_n%20%3D%20%5Csum%5E%7Bn%7D_%7Bi%3D1%7D%20a_i%3Da_1%2Ba_2%2B%20%5Ccdots%20%2Ba_n%24)
- Sum of the series - If the sequence is convergent and its limit exists as a real number, then the series is called convergent and we write ![$\sum^{\infty}_{n=1} a_n=s$](https://render.githubusercontent.com/render/math?math=%24%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20a_n%3Ds%24) The number _s_ is called the sum of the series. If the sequence is divergent, then the series is called divergent.
- A series ![$\sum a_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%20a_n%24) is called absolutely convergent if the series of absolute values ![$\sum \left| a_n \right|$](https://render.githubusercontent.com/render/math?math=%24%5Csum%20%5Cleft%7C%20a_n%20%5Cright%7C%24) is convergent.
- A series is called conditionally convergent if it is convergent but not absolutely convergent.
- A power series is a series of the form ![$\sum^{\infty}_{n=0} c_nx^n=c_0+c_1x+c_2x^2+ c_3x^3 + \cdots$](https://render.githubusercontent.com/render/math?math=%24%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D0%7D%20c_nx%5En%3Dc_0%2Bc_1x%2Bc_2x%5E2%2B%20c_3x%5E3%20%2B%20%5Ccdots%24) where _x_ is the variable, and the _c_'s are constants called the coefficients of the series.
  - If _c_ are all 1, the power series becomes the geometric series.
  - If replace _x_ with (_x - a_), it is called a power series in (_x - a_) or a power series centered at _a_ or a power series about _a_.
- Taylor’s Inequality - If ![$\left|f^{(n+1)}(x)\right| \leqslant M$](https://render.githubusercontent.com/render/math?math=%24%5Cleft%7Cf%5E%7B(n%2B1%29%7D(x%29%5Cright%7C%20%5Cleqslant%20M%24) for ![$|x-a| \leqslant d$](https://render.githubusercontent.com/render/math?math=%24%7Cx-a%7C%20%5Cleqslant%20d%24), then the remainder ![$R_n(x)$](https://render.githubusercontent.com/render/math?math=%24R_n(x%29%24) of the Taylor series satisfies the inequality ![$\left|R_n(x) \right| \leqslant \frac{M}{(n+1)!} |x-a|^{n+1}$](https://render.githubusercontent.com/render/math?math=%24%5Cleft%7CR_n(x%29%20%5Cright%7C%20%5Cleqslant%20%5Cfrac%7BM%7D%7B(n%2B1%29!%7D%20%7Cx-a%7C%5E%7Bn%2B1%7D%24) for ![$\left|x-a \right| \leqslant d$](https://render.githubusercontent.com/render/math?math=%24%5Cleft%7Cx-a%20%5Cright%7C%20%5Cleqslant%20d%24)
- The Binomial Series - If _k_ is any real number and _|x| < 1_, then ![$(1+x)^k = \sum^{\infty}_{n=0} \left( \begin{array}{c} k \ n \end{array} \right) x^n=1+kx+ \frac{k(k-1)}{2!} x^2+ \frac{k(k-1)(k-2)}{3!}x^3+ \cdots$](https://render.githubusercontent.com/render/math?math=%24(1%2Bx%29%5Ek%20%3D%20%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D0%7D%20%5Cleft(%20%5Cbegin%7Barray%7D%7Bc%7D%20k%20%5C%5C%20n%20%5Cend%7Barray%7D%20%5Cright%29%20x%5En%3D1%2Bkx%2B%20%5Cfrac%7Bk(k-1%29%7D%7B2!%7D%20x%5E2%2B%20%5Cfrac%7Bk(k-1%29(k-2%29%7D%7B3!%7Dx%5E3%2B%20%5Ccdots%24)
- P768

#### Properties

- Limit Laws for Sequences
  - P697
- The geometric series ![$\sum^{\infty}_{n=1} ar^{n-1}=a+ar+ar^2+ \cdots$](https://render.githubusercontent.com/render/math?math=%24%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20ar%5E%7Bn-1%7D%3Da%2Bar%2Bar%5E2%2B%20%5Ccdots%24) is convergent if _|r| < 1_ and its sum is ![$\frac{a}{1-r}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7Ba%7D%7B1-r%7D%24), if ![$\left|r \right| \geqslant 1$](https://render.githubusercontent.com/render/math?math=%24%5Cleft%7Cr%20%5Cright%7C%20%5Cgeqslant%201%24), the geometric series is divergent.
- The p-series ![$\sum^{\infty}_{n=1} \frac{1}{n^p}](https://render.githubusercontent.com/render/math?math=%24%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20%5Cfrac%7B1%7D%7Bn%5Ep%7D) is convergent if _p > 1_ and divergent if ![$p \leqslant 1$](https://render.githubusercontent.com/render/math?math=%24p%20%5Cleqslant%201%24)

## Theorem

- If ![$\lim_{n \to \infty} f(x)=L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20f(x%29%3DL%24) ![$f(n)=a_n$](https://render.githubusercontent.com/render/math?math=%24f(n%29%3Da_n%24) when _n_ is an integer, then ![$\lim_{n \to \infty} a_n=L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20a_n%3DL%24)
- If ![$\lim_{n \to \infty} \left|a_n \right|=0$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20%5Cleft%7Ca_n%20%5Cright%7C%3D0%24), then ![$\lim_{n \to \infty} a_n=0$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20a_n%3D0%24)
- If ![$\lim_{n \to \infty} a_n=L$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20a_n%3DL%24) and the function _f_ is continuous at _L_, then ![$\lim_{n \to \infty} f(a_n)=f(L)$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20f(a_n%29%3Df(L%29%24)
- The Squeeze Theorem can also be adapted for sequences.
- Monotonic Sequence theorem - Every bounded, monotonic sequence is convergent.
- If the series ![$\sum^{\infty}_{n=1} a_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20a_n%24) is convergent, then ![$\lim_{n \to \infty} a_n=0$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20a_n%3D0%24)
- If ![$\sum a_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%20a_n%24) and ![$\sum b_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%20b_n%24) are convergent series, then so are the series ![$\sum ca_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%20ca_n%24) (where c is a constant), ![$\sum (a_n+b_n)$](https://render.githubusercontent.com/render/math?math=%24%5Csum%20(a_n%2Bb_n%29%24) and ![$\sum (a_n-b_n)$](https://render.githubusercontent.com/render/math?math=%24%5Csum%20(a_n-b_n%29%24), and
  - ![$\sum^{\infty}_{n=1} ca_n=c \sum^{\infty}_{n=1} a_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20ca_n%3Dc%20%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20a_n%24)
  - ![$\sum^{\infty}_{n=1} (a_n+b_n)=\sum^{\infty}_{n=1} a_n + \sum^{\infty}_{n=1} b_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20(a_n%2Bb_n%29%3D%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20a_n%20%2B%20%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20b_n%24)
  - ![$\sum^{\infty}_{n=1} (a_n-b_n)=\sum^{\infty}_{n=1} a_n - \sum^{\infty}_{n=1} b_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20(a_n-b_n%29%3D%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20a_n%20-%20%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20b_n%24)
- Alternating Series Estimation Theorem - If ![$s = \sum (-1)^{n-1} b_n$](https://render.githubusercontent.com/render/math?math=%24s%20%3D%20%5Csum%20(-1%29%5E%7Bn-1%7D%20b_n%24), where ![$b_n > 0$](https://render.githubusercontent.com/render/math?math=%24b_n%20%3E%200%24), is the sum of an alternating series that satisfies [$b_{n+1} \leqslant b_n$](https://render.githubusercontent.com/render/math?math=%24b_%7Bn%2B1%7D%20%5Cleqslant%20b_n%24) and ![$\lim_{n \to \infty} b_n = 0$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20b_n%20%3D%200%24) then ![$\left|R_n \right| = \left|s - s_n \right| \leqslant b_{n+1}$](https://render.githubusercontent.com/render/math?math=%24%5Cleft%7CR_n%20%5Cright%7C%20%3D%20%5Cleft%7Cs%20-%20s_n%20%5Cright%7C%20%5Cleqslant%20b_%7Bn%2B1%7D%24)
- Theorem If a series is absolutely convergent, then it is convergent.
- For a given power series ![$\sum^{\infty}_{n=0} c_n(x-a)^n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D0%7D%20c_n(x-a%29%5En%24), there are only three possibilities:
  - The series converges only when _x = a_.
  - The series converges for all _x_.
  - There is a positive number R such that the series converges if `_|x - a| < R_` and diverges if `_|x - a| > R_`.
    - The number R is called the radius of convergence of the power series.
- Differentiation and integration of power Series - P754
- If _f_ has a power series representation (expansion) at _a_, that is, if ![$f(x)= \sum^{\infty}_{n=0} c_n (x-a)^n$](https://render.githubusercontent.com/render/math?math=%24f(x%29%3D%20%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D0%7D%20c_n%20(x-a%29%5En%24) _|x - a| < R_ then its coefficients are given by the formula ![$c_n = \frac{f^{(n)}(a)}{n!}$](https://render.githubusercontent.com/render/math?math=%24c_n%20%3D%20%5Cfrac%7Bf%5E%7B(n%29%7D(a%29%7D%7Bn!%7D%24)
  - subsititute coefficients formula into the power series returns the Taylor series ![$f(x)= \sum^{\infty}_{n=0} \frac{f^{(n)}(a)}{n!} (x-a)^n$](https://render.githubusercontent.com/render/math?math=%24f(x%29%3D%20%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D0%7D%20%5Cfrac%7Bf%5E%7B(n%29%7D(a%29%7D%7Bn!%7D%20(x-a%29%5En%24)
    - It returns the Taylor series of the function _f_ at _a_ (or about _a_ or centered at _a_)
    - When _a = 0_ it becomes Maclaurin series. ![$f(x)= \sum^{\infty}_{n=0} \frac{f^{(n)}(0)}{n!} x^n$](https://render.githubusercontent.com/render/math?math=%24f(x%29%3D%20%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D0%7D%20%5Cfrac%7Bf%5E%7B(n%29%7D(0%29%7D%7Bn!%7D%20x%5En%24)
- If ![$f(x)=T_n(x)+R_n(x)$](https://render.githubusercontent.com/render/math?math=%24f(x%29%3DT_n(x%29%2BR_n(x%29%24), where ![$T_n$](https://render.githubusercontent.com/render/math?math=%24T_n%24) is the nth-degree Taylor polynomial of _f_ at _a_ and ![$\lim_{n \to \infty} R_n(x) = 0$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20R_n(x%29%20%3D%200%24) for _|x - a| < R_, then _f_ is equal to the sum of its Taylor series on the interval _|x - a| < R_.

#### Methods

- Test for Divergence if ![$\lim_{n \to \infty} a_n$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20a_n%24) does not exist or if ![$\lim_{n \to \infty} a_n \neq 0$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20a_n%20%5Cneq%200%24), then the its series is divergent.
- The Integral Test - Suppose _f_ is a continuous, positive, decreasing function on ![$[1, \infty)$](https://render.githubusercontent.com/render/math?math=%24%5B1%2C%20%5Cinfty%29%24) and let ![$a_n=f(n)$](https://render.githubusercontent.com/render/math?math=%24a_n%3Df(n%29%24). Then the series ![$\sum^{\infty}_{n=1} a_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20a_n%24) is convergent if and only if the improper integral ![$\int^{\infty}_{1} f(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5E%7B%5Cinfty%7D_%7B1%7D%20f(x%29%20%5C%3B%20dx%24) is convergent. Otherwise the series is divergent.
- Remainder Estimate for the Integral Test - Suppose ![$f(k)=a_k$](https://render.githubusercontent.com/render/math?math=%24f(k%29%3Da_k%24) where _f_ is a continuous, positive, decreasing function for ![$x \geqslant n$](https://render.githubusercontent.com/render/math?math=%24x%20%5Cgeqslant%20n%24) and ![$\sum a_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%20a_n%24) an is convergent. If ![$R_n=s-s_n$](https://render.githubusercontent.com/render/math?math=%24R_n%3Ds-s_n%24), where _Sn_ is the partial(estimated) sum, then ![$\int^{\infty}_{n+1} f(x) ; dx \leqslant R_n \leqslant \int^{\infty}_{n} f(x) ; dx$](https://render.githubusercontent.com/render/math?math=%24%5Cint%5E%7B%5Cinfty%7D_%7Bn%2B1%7D%20f(x%29%20%5C%3B%20dx%20%5Cleqslant%20R_n%20%5Cleqslant%20%5Cint%5E%7B%5Cinfty%7D_%7Bn%7D%20f(x%29%20%5C%3B%20dx%24) where the remainder ![$R_n$](https://render.githubusercontent.com/render/math?math=%24R_n%24) represents the size the error. when ![$s_n$](https://render.githubusercontent.com/render/math?math=%24s_n%24), the sum of the first n terms, is used as an approximation to the total sum.
- The Comparison Test - Suppose that ![$\sum a_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%20a_n%24) and ![$\sum b_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%20b_n%24) are series with positive terms.
  - If ![$\sum b_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%20b_n%24) is convergent and ![$a_n \leqslant b_n$](https://render.githubusercontent.com/render/math?math=%24a_n%20%5Cleqslant%20b_n%24) for all _n_, then ![$\sum b_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%20b_n%24) is also convergent.
  - If ![$\sum b_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%20b_n%24) is divergent and ![$a_n \geqslant b_n$](https://render.githubusercontent.com/render/math?math=%24a_n%20%5Cgeqslant%20b_n%24) for all _n_, then ![$\sum b_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%20b_n%24) is also divergent.
- The Comparison Test - Suppose that ![$\sum a_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%20a_n%24) and ![$\sum b_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%20b_n%24) are series with positive terms. If ![$\lim_{n \to \infty} \frac{a_n}{b_n}=c$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20%5Cfrac%7Ba_n%7D%7Bb_n%7D%3Dc%24) where _c_ is a finite number and _c > 0_, then either both series converge or both diverge.
- Alternating Series Test - If the alternating series ![$\sum^{\infty}_{n=1} (-1)^{n-1} b_n=b_1-b_2+b_3-b_4+ \cdots ; ; ; b_n > 0$](https://render.githubusercontent.com/render/math?math=%24%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20(-1%29%5E%7Bn-1%7D%20b_n%3Db_1-b_2%2Bb_3-b_4%2B%20%5Ccdots%20%5C%3B%20%5C%3B%20%5C%3B%20b_n%20%3E%200%24) satisfies
  - [$b_{n+1} \leqslant b_n$](https://render.githubusercontent.com/render/math?math=%24b_%7Bn%2B1%7D%20%5Cleqslant%20b_n%24) for all _n_
  - ![$\lim_{n \to \infty} b_n = 0$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20b_n%20%3D%200%24) then the series is convergent.
- The Ratio Test
  - ![$\lim_{n \to \infty} \left| \frac{a_{n+1}}{a_n} \right| = L < 1$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20%5Cleft%7C%20%5Cfrac%7Ba_%7Bn%2B1%7D%7D%7Ba_n%7D%20%5Cright%7C%20%3D%20L%20%3C%201%24), then the series ![$\sum^{\infty}_{n=1} a_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20a_n%24) is absolutely convergent, and therefore convergent.
  - If ![$\lim_{n \to \infty} \left| \frac{a_{n+1}}{a_n} \right| = L > 1$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20%5Cleft%7C%20%5Cfrac%7Ba_%7Bn%2B1%7D%7D%7Ba_n%7D%20%5Cright%7C%20%3D%20L%20%3E%201%24) then the series ![$\sum^{\infty}_{n=1} a_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20a_n%24) is divergent.
  - ![$\lim_{n \to \infty} \left| \frac{a_{n+1}}{a_n} \right| =  1$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20%5Cleft%7C%20%5Cfrac%7Ba_%7Bn%2B1%7D%7D%7Ba_n%7D%20%5Cright%7C%20%3D%20%201%24) the Ratio Test is inconclusive; that is, no conclusion can be drawn about the convergence or divergence of ![$\sum^{\infty}_{n=1} a_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20a_n%24).
- The Root Test
  - If ![$\lim_{n \to \infty} \sqrt[n]{\left| a_n \right|}=L < 1 $](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20%5Csqrt%5Bn%5D%7B%5Cleft%7C%20a_n%20%5Cright%7C%7D%3DL%20%3C%201%20%24), then the series ![$\sum^{\infty}_{n=1} a_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20a_n%24) is absolutely convergent, and therefore convergent.
  - If ![$\lim_{n \to \infty} \sqrt[n]{\left| a_n \right|}=L > 1 $](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20%5Csqrt%5Bn%5D%7B%5Cleft%7C%20a_n%20%5Cright%7C%7D%3DL%20%3E%201%20%24) or ![$\lim_{n \to \infty} \sqrt[n]{\left| a_n \right|}=\infty$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20%5Csqrt%5Bn%5D%7B%5Cleft%7C%20a_n%20%5Cright%7C%7D%3D%5Cinfty%24) then the series ![$\sum^{\infty}_{n=1} a_n$](https://render.githubusercontent.com/render/math?math=%24%5Csum%5E%7B%5Cinfty%7D_%7Bn%3D1%7D%20a_n%24) is divergent.
  - If ![$\lim_{n \to \infty} \sqrt[n]{\left| a_n \right|}=1$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bn%20%5Cto%20%5Cinfty%7D%20%5Csqrt%5Bn%5D%7B%5Cleft%7C%20a_n%20%5Cright%7C%7D%3D1%24), the Root Test is inconclusive.
