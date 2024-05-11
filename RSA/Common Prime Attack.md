# COMMON PRIME ATTACK
Using this attack we can find the prime factors of the public modulus if there are multiple moduli being generated using a faulty modulus generator.

**STEPS** : 

1. From the set of retrieved moduli, find a pair of moduli N1, N2 which satisfy the following condition: $$GCD(N1, N2)!=1$$ If this is satisfied, it means that the corresponding moduli have a number in common i.e. the common prime.
2. Then calculate the common prime as $$p = GCD(N1, N2)$$ $$q1 = N1/p$$ $$q2 = N2/p$$

4. Calculate the corresponding private keys as $$d1 = mod inverse(e, (p-1)(q-1))$$ and $$d2 = modinverse(e, (p-1)(q-1))$$ where modinverse(a, b) ⇒ Modular multiplicative inverse of a over b.
