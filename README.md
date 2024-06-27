# CPU
My Self-Made CPU with Logisim inside *cpu.circ*

# How to view it?
- To open the file *cpu.cir* with the application ***Logisim***. Which is a free software written in Java.

# Each file explanation 

1. half adder
- 1-bit half adder, which takes two inputs **A** (1-bit) and **B** (1-bit).
- output **sum** (1-bit)
- output **carry** (1-bit)
- Possible values:

| A | B | sum | carry |
| :-- | :-- | :-- | :-- |
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 |

2. full adder
- 1-bit full adder, which takes three inputs **A**, **B**, and **carry in**
- two 1-bit outputs **sum** and **carry out**
- Possible values:

| A | B | carry in | sum | carry out |
| :-- | :-- | :-- | :-- | :-- |
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

- In short, if the three inputs are all *0*, then the two outputs will all be *0*.
- If the three inputs have one *1*, then the **sum** will be *1* and **carry out** will be *0*.
- If the three inputs have two *1*s, then the **sum** will be *0* and **carry out** will be *1*.
- If the three inputs all are *1*, then the two outputs will both be *1*.

3. 8 bit full adder
- Inputs: **A** of 8-bit, **B** of 8-bit, **carry in** of 1-bit.
- Outputs: **sum** of 8-bit, **carry out** of 1-bit.
- Philosophy behind it: it consists of multiple previous ***full adder*** we've defined beforehand.

4. 16 bit full adder
- Same similar logic as the ***8 bit full adderr***.



