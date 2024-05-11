## DSA

- Signing
    * p = Prime
    * x, k, g = random(1,p) numbers
    * y = g ^ x mod p
    * r = g ^ k mod p
    * s = (k-1(H(m) + xr))
    * H => secure hash function
    * m => message

- Verify
    * r = (g ^ H(m) y ^ r)s ^ -1
    * g ^ H(m) y ^ r = g ^ (H(m)+xr) = g ^ ks, and so (g ^ H(m) y ^ r)s ^ -1 = g ^ k = r

## ECDSA

- Signing
    * p = Prime
    * x,k = random(1,p) numbers
    * g => elliptic curve point
    * y = g ^ x => POINT ON THE ELLIPTIC CURVE
    * r = x(g ^ k) => x value of the point
    * s = (k-1(H(m) + xr))

- Verify
    * g ^ H(m) y ^ r = g ^ (H(m)+xr) = g ^ ks, and so (g ^ H(m) y ^ r)s ^ -1 = g ^ k
    * x(g ^ k) = r