# CH 02 Number Theory

[toc]

## Euclidean Algorithm

### Modulus

### Congruences

#### Congruent Modulo n

#### Properties of  Congruences

- Congruences have the following properties:

  1. **$a  \equiv  b\:( \mod n) \quad iff \quad n\: |\:(a\:-\:b\:)\:$**

     >
     >
     >Demonstrate:
     >
     >​	$if\quad  n\:|\:(a-b), \quad then \quad (a-b)\:=\:kn \quad for\:some \quad k$
     >
     >​	$so \quad write \quad a = b + kn$
     >
     >​	$therefore$
     >
     >​	$(a \mod n) = (remainder\quad when \quad b\: +\:kn \quad is \quad is \quad divided\quad by \quad n)$
     >
     >​	$= (remainder \quad when \quad b \quad is \quad divided \quad by \quad n) = (b \mod n)$
     >
     >
     >
     >例子：
     >
     >$23 \equiv 8 (\mod 5) \quad because \quad 23 - 8 = 15 = 5 * 3$
     >
     >$-11 \equiv 5 (\mod 8) \quad because \quad -11 - 5 = -16 = 8 * (-2)$
     >
     >$81 \equiv 0 (\mod 27) \quad because \quad 81 - 0 = 81 = 27 * 3$
     >
     >

  2. **$a \equiv b\:(\mod n) \quad imply \quad b \equiv a\:(\mod n)$**

  3. **$ a \equiv b\: (\mod n) \quad and \quad b \equiv c(\mod n) \quad imply \quad a \equiv c(\mod n)$**

- Modular arithmetic exhibits the following properties:

  1. **$[(a\mod n)+(b\mod n)]\mod n = (a+b) \mod n $**

     >
     >
     >Demonstrate:
     >
     >- Define $(a\mod n) = r_a $ and $(b\mod n) = r_b$. 
     >
     >  Then we can write $a = r_a + jn \quad for\quad some\quad integer\quad j$ and $b=r_b+kn\quad for\quad some\quad integer\quad k$
     >
     >- Then:
     > $$
     >  \begin{align}
     >  (a+b)\mod n &= (r_a+jn+r_b+kn)\mod n \\ &= (r_a + r_b+(k+j)n)\mod n\\&=(r_a+r_b)\mod n \\&= [(a\mod n) + (b \mod n)]\mod n
     >  \end{align}
     > $$
     > 

  2. **$[(a \mod n)-(b \mod n)]\mod n = (a-b)\mod n$**

  3. **$[(a\mod n)*(b\mod n)]\mod n = (a*b)\mod n$**
  
  - Examples of the three properties:
  
    ![](Resources\01.jpg)
  
    ![](Resources\02.jpg)
  
    ![](Resources\03.jpg)

### Extended Euclidean Algorithm Example

Problem:

​	GCD(1759, 550) = 1

​	We can find x and y , s.t. 1759x + 550y = GCD(1759, 550) = 1

​	The extended Euclidean algorithm finds these x and y.



Generalize: 

​	Given 𝑎 and 𝑏 (𝑎 > 𝑏), 

​	Find 𝑥, 𝑦, 𝑑 , s.t. 𝑎𝑥 + 𝑏𝑦 = 𝑑 = 𝐺𝐶𝐷(𝑎, 𝑏). 

​	We keep two invariant equations:

​	$ax_1+by_1=d_1$

​	$ax_2+by_2=d_2$

​	Begin with (𝑥1, 𝑦1, 𝑑1) = (1,0, 𝑎) and (𝑥2, 𝑦2, 𝑑2) = (0,1, 𝑏) and 

​	keep reducing the right-hand side of the equations until it reaches 0.



Example with 𝑎 = 1759, 𝑏 = 550 -> Result: d = 1; x = –111; y = 355

![](Resources\00.jpg)

![](Resources\04.jpg)

![](Resources\05.jpg)

## Prime Numbers

- Prime numbers only have divisors of 1 and itself.

  It means that prime numbers cannot be written as a product of other numbers.

- Prime numbers are central to number theory.

- Any integer a > 1 can be factored in a unique way as 
  $$
  a = p_1^{a_1} * p_2^{a_2}*...*p_t^{a_t}
  $$
  where $p_1<p_2<...<p_t$ are prime numbers and where each $a_i$ is a positive integer.

- This is known as the fundamental theorem of arithmetic.

### Fermat's Theorem

- States the following:

  If p is prime and a is a positive integer not divisible by p then

$$
a^{p-1}\equiv1(\mod p)
$$

- An alternate form is:

  If p is prime and a is a positive integer then
  $$
  a^p\equiv a(\mod p)
  $$

### Euler Totient Function $\phi(n)$

- The number of positive integers up to n that are relatively prime to n.

![](Resources\06.jpg)

- Properties:

  1. $\phi(p) = p - 1 , \quad where\quad p \quad is \quad prime$

     >E.g.
     >
     >$\phi(3)=2$
     >
     >$\phi(5)=4$
     >
     >$\phi(7)=6$

  2. $\phi(n)=(p-1)(q-1),\quad where \quad n = p*q\quad and \quad p,q \quad are \quad both \quad prime \quad numbers.$

     >E.g.
     >
     >$\phi(15) = (3 - 1) * (5-1)=8$
     >
     >$\phi(21) = (3 - 1) * (7-1)=12$

### Euler's Theorem

- States that for every a and n that are relatively prime:
  $$
  a^{\phi(n)}\equiv1(\mod n)
  $$

- An alternative form is:

$$
a^{\phi(n)+1}\equiv a(\mod n)
$$



