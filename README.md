# Turing Machine - 0<sup>2<sup>n</sup></sup>

## 
Created a Turing Machine using YAML language to decide the language 0<sup>2<sup>n</sup></sup>


### Template by  [Daniel Chahine](https://github.com/DanielChahine0)
<hr>

This Turing machine decides the language L(M)={0<sup>2<sup>n</sup></sup> | n≥0}

The Machine could be viewd using [THIS LINK](https://turingmachine.io/?import-gist=c3b690296cab1e62886aba56402b0ea5)

## The machine is split into 3 parts:
> # Start & Accept
The machine start by crossing of the first 0 from the tape. If the tape doesn't start with 1, it dies and does not get accepted. If it has only one 0 then just accept immediatly
```
q1:
    0: {write: ' ', R: q2}

q2:
    X: R
    ' ': {R: accept}
    0: {write: X, R: q3}

accept:
    # EMPTY STATE
```
<br>

> # Crossor
This part cross off every other 0 in the tape resulting in a recursive pattern. This is a crucial step as it allows us to know not only the even number of zero's but to only accept the 0's that are a multiple of 2.
```
q3:
    X: R
    ' ': {L: q5}
    0: {R: q4}

q4:
    X: R
    0: {write: X, R: q3}
```

<br>

> # Recursive
When we finish crossing off every 0, we go back to the beginning of the tape and repeat the process until every 0 is crossed.

NOTE: when crossing off the 0's for the 2nd+ time we don't cross off the other half that was not crossed. We go recursively cross off every other 0 remaining. 

I hope this example will help: 0000000000000000 → 
X0X0X0X0X0X0X0X → XXX0XXX0XXX0XXX → XXXXXXX0XXXXXXX → XXXXXXXXXXXXXXX


```
q5:
    0: L
    X: L
    ' ': {R: q2}
```

<br>
<hr>
<hr>

This is not supposed to be the **perfect solution** or the most efficient one, this is just **my way** of doing this challenge, feel free to improve my Turing Machine and play with its parameters.


```
Daniel Chahine
```