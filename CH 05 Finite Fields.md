# Chapter 5 Finite Fields

[toc]

## Review of Chapter 2 Number Theory

- Divisor, multiple, division algorithm 
- GCD and Euclid algorithm 
- Modular arithmetic 
- Extended Euclid algorithm and multiplicative inverse 
- Prime numbers 
- Fermat (little) theorem 
- Euler totient function 𝜙(𝑛) 
- Euler theorem 
- Primality test 
- Powers of integers modulo p and group generator 
- Discrete logarithm

## Group and Field

### Groups

- A set of elements with a binary operation denoted by $\cdot$ that associates to each ordered pair (a,b) of elements in G an element (a $\cdot$ b ) in G
- Exponentiation is defined within a group as a repeated application of the group operator, so that $a^3 = a\cdot a\cdot a$.
-  Define $a^0=e$ as the identity element, and $a^{-n}={a^{'}}$ is the inverse element of a within the group.

### Axioms

- (A1) Closure:

  - If a and b belong to G, then $a\cdot b$ is also in G.

- (A2) Associative:

  - $a\cdot(b\cdot c) = (a\cdot b)\cdot c\quad for\ all\quad a,b,c\quad in\quad G.$

- (A3) Identity Element:

  - There is an element e in G such that $a\cdot e=e\cdot a=a\quad for\quad all\quad a\quad in\quad G.$

- (A4) Inverse Element:

  - For each a in G,there is an element $a^{-1}$ in G such that $a\cdot a^{-1}=a^{-1}\cdot a=e.$

-  Abelian Group:

  (A5) Commutative:

  - $a\cdot b=b\cdot a\ for\quad all\quad a,b\quad in\quad G.$

### Cyclic Group

- A group G is **cyclic** if every element of G is power $a^k(k\quad is\quad an\quad integer)$ of a fixed element a **$a\ \euro\ G$**.
- The element a is said to **generate** the group G or to be a generator of G.
- A cyclic group is always abelian and may be finite or infinite.

## Finites

- A field F , sometimes denoted by {F, +,* }, is a set of elements with two binary operations, called addition and multiplication, such that for all a, b, c in F the following axioms are obeyed:

  - **(A1–A5)** 

    F satisfies axioms A1 through A5 and the same for multiplication. (abelian group for add and mult)

  - **No zero divisors:**

    If a,b in F and ab = 0, then either a = 0 or b = 0.

  - **Distributive law**

- In essence, a field is a set in which we can do addition, subtraction, multiplication, and division without leaving the set. Division is defined with the following rule: $a /b = a (b-1 )$

- Familiar examples of fields are the rational numbers, the real numbers, and the complex numbers. Note that the set of all integers is not a field, because not every element of the set has a multiplicative inverse.

### Finite Field

Finite fields play a crucial role in many cryptographic algorithms

#### Prime Field GF(p)

The order of a finite field must be a power of a prime p n , where n is a positive integer

- The finite field of order $p^n$ is generally written $GF(p^n)$
- GF stands for Galois Field, in honor of the mathematician who first studied finite fields

##### Polynomial Division

- The form of Polynomial:

  $f(x) = q(x)g(x)+r(x) $

  - $r(x)$ can be interpreted as begin a remainder
  - So $r(x)=f(x)\mod g(x)$

- If there is no remainder we can say $g(x)$ **divides** $f(x)$

  - Written as $g(x)\ |\ f(x)$
  - Say that $g(x)$ is a **factor** of $f(x)$  or $g(x)$ is a **divisor** of $f(x)$

- A polynomial $f(x)$ over a field F is called **irreducible** if and only if $f(x)$ cannot be expressed as a product of two polynomials, both over F, and both of degree lower than that of $f(x)$

  - An irreducible polynomial is also called a **prime polynomial**

##### Polynomial GCD

- The polynomial c(x) is said to be the greatest common divisor of a(x) and b(x) if the following are true:
  - c(x) divides both a(x) and b(x)
  - any common divisor of a(x) and b(x) is a divisor of c(x)
- The Euclidean algorithm can be extended to find the greatest common divisor of two polynomials whose coefficients are elements of a field.
- The extended Euclidean algorithm can be extended to find the multiplicative inverse of a polynomial modulo an irreducible polynomial.

#### Binary Field GF($2^n$)

- Number of elements : $2^n$
- Elements are represented as binary polynomials with n coefficients.
- Polynomial arithmetic with coefficients in $Z_2$
- Polynomial arithmetic with reduction modulo an irreducible polynomial of degree n

##### Computational Considerations

- Since coefficients are 0 or 1, they can represent any such polynomial as a bit string
- Addition becomes XOR of these bit strings
- Multiplication is shift and XOR 
  -  no long-hand multiplication
- Modulo reduction is done by repeatedly substituting highest power with remainder of irreducible polynomial (also shift and XOR)
- Example:

$$
\begin{align}
& (x^2+1) \times(x^2+x+1)\mod (x^3+x+1)\\\\
& \cdot Fact:\quad x^3\mod(x^3+x+1)=x+1\\\\

& \cdot (x^2+1)\times x\mod (x^3+x+1) \\
& =(x^3+x)\mod (x^3+x+1)\\
& =((x+1)+x)\mod (x^3+x+1)\\
& = 1.\\\\

& \cdot (x^2+1) \times x^2\mod (x^3+x+1)\\
& = ((x^2+1)\times x\mod(x^3+x+1))\times x\mod(x^3+x+1)\\
& = 1\times x\mod (x^3+x+1)\\
& = x.\\\\

& \cdot(x^2+1) \times (x^2+x+1)\mod (x^3+x+1) \\
& = [(x^2+1)\times x^2+(x^2+1)\times x+(x^2+1)\times 1]\mod (x^3+x+1)\\
& = [x+1+(x^2+1)]\mod (x^3+x+1)\\
& = x^2+x.
\end{align}
$$



## Efficient Computation on Finite Field

