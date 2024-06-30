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

### 3. 8 bit full adder
- Inputs: **A** of 8-bit, **B** of 8-bit, **carry in** of 1-bit.
- Outputs: **sum** of 8-bit, **carry out** of 1-bit.
- Philosophy behind it: it consists of multiple previous ***full adder*** we've defined beforehand.

- Pin:
    1. **A** : West edge, upper pin. (input, bit width 8)
    2. **B** : West edge, middle pin. (input, bit width 8)
    3. **carry in** : West edge, lower pin. (input, bit width 1)
    4. **sum** : East edge, upper pin. (output, bit width 8)
    5. **carry out** : East edge, lower pin. (output, bit width 1)

### 4. 16 bit full adder
- Pin:
    1. **A** : West edge, upper pin. (input, bit width 16)
    2. **B** : West edge, middle pin. (input, bit width 16)
    3. **carry in** : West edge, lower pin. (input, bit width 1)
    4. **sum** : East edge, upper pin. (output, bit width 16)
    5. **carry out** : East edge, lower pin. (output, bit width 1)

### 5. 16 bit full subtractor
- Pin:
    1. **A** : West edge, upper pin. (input, bit width 16)
    2. **B** : West edge, middle pin. (input, bit width 16)
    3. **carry in** : West edge, lower pin. (input, bit width 1)
    4. **sum** : East edge, upper pin. (output, bit width 16)
    5. **carry out** : East edge, lower pin. (output, bit width 1)

### 6. 16 bit 2's complement
- Pin:
    1. **IN** : North edge. (input, bit width 16)
    2. **EN** : East edge. (input, bit width 1) 
    3. **OUT** : South edge. (input, bit width 16)

### 7. 1 bit memory cell
- Pin:
    1. **IN** : West edge, upper pin. (input, bit width 1)
    2. **SET** : West edge, lower pin. (input, bit width 1)
    3. **Q** : East edge. (output, bit width 1)

### 8. 1 byte (8 bit) memory cell
- Pin:
    1. **IN** : West edge, upper pin. (input, bit width 8)
    2. **EN** : West edge, lower pin. (input, bit width 1)
    3. **Q** : East edge. (output, bit width 8)

### 9. 2 byte (16 bit) memory cell
- Pin:
    1. **IN** : West edge, upper pin. (input, bit width 16)
    2. **EN** : West edge, lower pin. (input, bit width 1)
    3. **Q** : East edge. (output, bit width 16)

### 10. 3 byte (24 bit) memory cell
- Pin:
    1. **IN** : West edge, upper pin. (input, bit width 24)
    2. **EN** : West edge, lower pin. (input, bit width 1)
    3. **Q** : East edge. (output, bit width 24)

### 11. 8 bit enable cell
- Pin:
    1. **IN** : West edge, upper pin. (input, bit width 8)
    2. **EN** : West edge, lower pin. (input, bit width 1)
    3. **OUT** : East edge. (output, bit width 8)

### 12. 16 bit enable cell
- Pin:
    1. **IN** : West edge, upper pin. (input, bit width 16)
    2. **EN** : West edge, lower pin. (input, bit width 1)
    3. **OUT** : East edge. (output, bit width 16)

### 13. 8 bit register
- Pin:
    1. **IN** : West edge, upper pin. (input, bit width 8)
    2. **SET** : West edge, lower pin. (input, bit width 1)
    3. **EN** : East edge, lower pin. (input, bit width 1)
    4. **OUT** : East edge, upper pin. (output, bit width 8)
    5. North pin : display the value inside register. (output, bit width 8)

### 14. 16 bit register
- Pin:
    1. **IN** : West edge, upper pin. (input, bit width 16)
    2. **SET** : West edge, lower pin. (input, bit width 1)
    3. **EN** : East edge, lower pin. (input, bit width 1)
    4. **OUT** : East edge, upper pin. (output, bit width 16)
    5. North pin : display the value inside register. (output, bit width 16)

### 15. 24 bit register
- Pin:
    1. **IN** : West edge, upper pin. (input, bit width 24)
    2. **SET** : West edge, lower pin. (input, bit width 1)
    3. **EN** : East edge, lower pin. (input, bit width 1)
    4. **OUT** : East edge, upper pin. (output, bit width 24)
    5. North pin : display the value inside register. (output, bit width 24)

### 16. 2x4 decoder
### 17. 3x8 decoder
### 18. 4x16 decoder

### 19. 8 bit reverter
- Behavior:
    - it will revert the input, e.g. 1000 0001 ==> 0111 1110
- Pin:
    1. West edge. (input, bit width 8)
    2. East edge. (output, bit width 8)

### 20. 16 bit reverter
- Behavior:
    - it will revert the input, e.g. 0001 0001 0001 0001 ==> 1000 1000 1000 1000
- Pin:
    1. West edge. (input, bit width 16)
    2. East edge. (output, bit width 16)

### 21. 8 bit negator
- Behavior:
    - it will flip the MSB.
- Pin:
    1. West edge. (input, bit width 8)
    2. East edge. (output, bit width 8)

### 22. 16 bit negator
- Behavior:
    - it will flip the MSB.
- Pin:
    1. West edge. (input, bit width 16)
    2. East edge. (output, bit width 16)

### 23. 8 bit right shifter

### 24. 16 bit right shifter

### 25. 8 bit left shifter

### 26. 16 bit left shifter

### 27. 1 bit comparator

### 28. 8 bit comparator

### 29. 16 bit comparator

### 30. 8 bit bus1

### 31. 16 bit bus1

### 32. 16 bit clear

### 33. 1 bit temp

### 34. 8 bit temp

### 35. 16 bit temp

### 36. 16 bit lower mask

### 37. 8 bit accumulator

### 38. 16 bit accumulator

### 39. 8 bit AND

### 40. 16 bit AND

### 41. 8 bit OR

### 42. 16 bit OR

### 43. 8 bit XOR

### 44. 16 bit XOR

### 45. 8 bit zero checker

### 46. 16 bit zero checker

### 47. 16 bit parity check

### 48. 16 bit negativity check

### 49. 16 bit positivity check

### 50. 8 bit ALU

### 51. 16 bit ALU

### 52. cpu clock

### 53. 8-step stepper

### 54. 16-step stepper

### 55. 16 bit FLAGS

### 56. 16 bit IR

### 57. 7 segement display demo

### 58. counter

### 59. cpu control section

### 60. cpu

### 61. cpu demo







