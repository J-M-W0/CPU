# CPU
My Self-Made CPU with Logisim inside *cpu.circ*

# How to view it?
- To open the file *cpu.cir* with the application ***Logisim***. Which is a free software written in Java.

# Each file explanation 

### 1. half adder
- Behavior:
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

- Pin:
    1. **A** : West edge, upper pin. (input, bit width 1) 
    2. **B** : West edge, lower pin. (input, bit width 1)
    3. **sum** : East edge, upper pin. (output, bit width 1)
    4. **carry** : East edge, lower pin. (output, bit width 1)

### 2. full adder
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
- If the three inputs have two 1s, then the **sum** will be *0* and **carry out** will be *1*.
- If the three inputs all are *1*, then the two outputs will both be *1*.

- Pin:
    1. **A** : West edge, upper pin. (input, bit width 1)
    2. **B** : West edge, middle pin. (input, bit width 1)
    3. **carry in** : West edge, lower pin. (input, bit width 1)
    4. **sum** : East edge, upper pin. (output, bit width 1)
    5. **carry out** : East edge, lower pin. (output, bit width 1)

3. 8 bit full adder
- Inputs: **A** of 8-bit, **B** of 8-bit, **carry in** of 1-bit.
- Outputs: **sum** of 8-bit, **carry out** of 1-bit.
- Philosophy behind it: it consists of multiple previous ***full adder*** we've defined beforehand.

- Pin:
    1. **A** : West edge, upper pin. (input, bit width 8)
    2. **B** : West edge, middle pin. (input, bit width 8)
    3. **carry in** : West edge, lower pin. (input, bit width 1)
    4. **sum** : East edge, upper pin. (output, bit width 8)
    5. **carry out** : East edge, lower pin. (output, bit width 1)

4. 16 bit full adder
- Pin:
    1. **A** : West edge, upper pin. (input, bit width 16)
    2. **B** : West edge, middle pin. (input, bit width 16)
    3. **carry in** : West edge, lower pin. (input, bit width 1)
    4. **sum** : East edge, upper pin. (output, bit width 16)
    5. **carry out** : East edge, lower pin. (output, bit width 1)

5. 16 bit full subtractor
- Pin:
    1. **A** : West edge, upper pin. (input, bit width 16)
    2. **B** : West edge, middle pin. (input, bit width 16)
    3. **carry in** : West edge, lower pin. (input, bit width 1)
    4. **sum** : East edge, upper pin. (output, bit width 16)
    5. **carry out** : East edge, lower pin. (output, bit width 1)

6. 16 bit 2's complement
- Pin:
    1. **IN** : North edge. (input, bit width 16)
    2. **EN** : East edge. (input, bit width 1) 
    3. **OUT** : South edge. (input, bit width 16)

7. 1 bit memory cell
- Pin:
    1. **IN** : West edge, upper pin. (input, bit width 1)
    2. **SET** : West edge, lower pin. (input, bit width 1)
    3. **Q** : East edge. (output, bit width 1)

8. 1 byte (8 bit) memory cell
- Pin:
    1. **IN** : West edge, upper pin. (input, bit width 8)
    2. **EN** : West edge, lower pin. (input, bit width 1)
    3. **Q** : East edge. (output, bit width 8)

9. 2 byte (16 bit) memory cell
- Pin:
    1. **IN** : West edge, upper pin. (input, bit width 16)
    2. **EN** : West edge, lower pin. (input, bit width 1)
    3. **Q** : East edge. (output, bit width 16)

10. 3 byte (24 bit) memory cell
- Pin:
    1. **IN** : West edge, upper pin. (input, bit width 24)
    2. **EN** : West edge, lower pin. (input, bit width 1)
    3. **Q** : East edge. (output, bit width 24)



