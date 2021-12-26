# Process Engineering Project

Project for testing the implementation of different Process Engineering concepts.

### Attention:
**I haven't yet studied the technical vocabulary in english for this subject.
It may occur that some translations are imprecise or incorrect.**

This started as a code for implementing an equation ordering algorithm (EOA).
A complex process engineering problem contains many equations that must be
solved for a complete description of the system. This modeling establishes
an algorithm for picking the order in which the equations are solved in
order to minimize the computational burden.

This inspired me to attempt to develop the algorithm in such a way that it
fetches the equations' variables automatically. Equations are defined
as functions, the values of which should equal zero. For 
example, equation
x<sub>1</sub> + x<sub>2</sub>(x) = 1 will be represented as
f(x) = x<sub>1</sub> + x<sub>2</sub>(x) - 1.

```
def f(x1, x2):
    return x1 + x2 - 1
    
_ = aoe2(f)
# Just by passing f, the algorithm is able to identify
# that its arguments are x1 and x2.
# This is done through the inspect module.
```

Another algorithm I intend on implementing is a procedure for choosing the order
in which the system's equipments are to be simulated. Each equipment has its own
set of equations, that themselves are ordered through the EO algorithm. Since
the equipments are interconnected in a complex manner, the order in which they
are solved can also be optimized to minimize computational burden, but the
algorithm is a little different.

This is what is pushing me to develop classes for representing streams and
equipments, so that I can integrate them more easily, and in the future
integrate both approaches. A highlight is that the `Flow` class (that represents
process streams) dynamically generates its `restriction` method in a way that it
can be used by the equation ordering algorithm (given a few details) and also
represent an unique equation for only that process stream.
