## COMMON MODULUS ATTACK

works when same plaintext is encrypted in 2 different ways with same modulus but different public exponent

$$
c1 = m ^ e mod (n) \\ c2 = m^E mod (n)
$$

### Bezout’s identity

$$
(e * a) + (E * b) = GCD(e, E)
$$

a and b can be found using Extended Euclidean Algorithm

## `c1 ^ a = m ^ (e * a) mod n`

## `c2 ^ b = m ^ (E * b) mod n`

## `c1 ^ a * c2 ^ b = m ^ GCD(e, E) mod n`
