# SMARTS ATTACK

- To compute elliptic curve discrete logarithm problem (ECDLP)
- When E.order() == p (prime which the elliptic curve is defined)
- Curve should have trace of Frobenius = 1 => Implies the no of points on the curve is equal to p

This attack relies on the specific properties of curves that have an order equal to the base field, as well as the trace of Frobeniusor the cardinality of the curve equal to the base field. The attack is based on the idea of reducing the problem to solving a system of polynomial equations, and these specific properties of the curve allow for an efficient reduction.

```py
from sage.all import *

def _lift(E, P, gf):
    x, y = map(ZZ, P.xy())
    for point_ in E.lift_x(x, all=True):
        _, y_ = map(gf, point_.xy())
        if y == y_:
            return point_

def attack(G,P):
    E = G.curve()
    gf = E.base_ring()
    p = gf.order()
    assert E.trace_of_frobenius() == 1, f"Curve should have trace of Frobenius = 1."

    E = EllipticCurve(Qp(p), [int(a) + p * ZZ.random_element(1, p) for a in E.a_invariants()])
    G = p * _lift(E, G, gf)
    P = p * _lift(E, P, gf)
    Gx, Gy = G.xy()
    Px, Py = P.xy()
    return int(gf((Px / Py) / (Gx / Gy)))
```
- The function takes in two points G and P on an elliptic curve E, and the base field gf of the curve.

- The x and y coordinates of the point P are mapped to integers using the ZZ function.

- The function Hlift(hensel lifting) is called to find the point P on the elliptic curve E in the ring of p-adic numbers.

- The order of the curve and the order of the base field are checked to make sure they are equal.

- The curve E is changed to a rational field and then to a field of p-adic numbers, and the points G and P are scaled by a factor of p.

- The x and y coordinates of the points G and P are obtained, and the ratio of the x and y coordinates of P and G is calculated.

- The result of the calculation is cast to an integer and returned as the solution to the ECDLP.