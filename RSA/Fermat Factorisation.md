# FERMAT FACTORISATION
The algorithm allows efficiently calculating the prime factors of a composite number that is the product of two close primes.

The idea of Fermat's factorization algorithm is that a product of two large primes can always be written as $$N=(a-b)*(a+b)$$ with a being the middle between the two primes and b the distance from the middle to each of the primes.

If the primes are close then a is close to the square root of N. This allows guessing the value a by starting with the square root of N and then incrementing the guess by one each round.

For each guess we can calculate $$b^2 = a^2 - N$$ If the result is a square we know we have guessed a correctly. From this we can calculate $$p=a+b$$ and $$q=a-b$$.

```python
def basic_fermat(n):
    a = ceil(sqrt(n))
    b2 = a^2 - n
    while not is_square(b2):
        a += 1
        b2 = a^2 - n
    return (a-sqrt(b2), a+sqrt(b2))
```
