# Custom CPU on Logisim

This project demonstrates a custom CPU designed and implemented using Logisim. 
Logisim is an educational tool for designing and simulating digital logic circuits, 
and this project showcases a CPU built from scratch, including its instruction set, control unit, and data paths etc.

## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [File Structure](#file-structure)
- [Example](#example)
- [Components](#components)
- [Instruction Set](#instruction-set)
- [Demonstration Video](#demonstration-video)
- [Contributing](#contributing)
- [License](#license)

## Introduction

This project involves the design and simulation of a custom Von Neumann Architecture CPU using Logisim. 
The CPU supports a variety of instructions and is capable of performing basic arithmetic operations, memory access, and control flow operations. 
This project is an educational tool aimed at helping students and enthusiasts understand CPU architecture and digital logic design.

## Features

- **Custom Instruction Set**: A unique set of instructions tailored for this CPU.
- **Arithmetic Operations**: Supports basic arithmetic operations like addition, subtraction, multiplication, and division.
- **Memory Access**: Instructions for loading from and storing to memory.
- **Control Flow**: Instructions for conditional and unconditional branching.
- **Modular Design**: Clear separation of the control unit, ALU, registers, and memory.

## Installation

To work with this project, you need to have __Logisim__ installed on your system. 
You can download Logisim from [the official website](http://www.cburch.com/logisim/).

1. Download and install Logisim:
    - **Windows/Mac/Linux**: Follow the installation instructions provided on the Logisim website.

2. Clone the repository:
    ```sh
    git clone <repo>
    ```
3. Navigate to the project directory:
    ```sh
    cd <repo-directory>
    ```

## Usage

1. **Open Logisim**: Launch Logisim on your computer.
2. **Load the Project**: Open the Logisim project file (`cpu.circ`) located in the project directory.
3. **Simulate the CPU**: Use Logisim's simulation features to test and observe the behavior of the CPU. You can load different programs into memory and step through their execution using the control panel.

## File Structure

- `cpu.circ`: The main Logisim circuit file for the custom CPU.
- `instructions.circ` The Logisim file containing the control flow of each instruction set.
- `README.md`: This file.
- `LICENSE`: License file for the project.

## Example

To see a simple program running on the CPU:

1. Open `cpu.circ` in Logisim.
2. Retrieve an example program file (`a.txt`) from the [RASM](https://github.com/J-M-W0/Assembler) project.
3. Load the example program file (`a.txt`) into the CPU's memory.
4. Run the simulation and observe how the CPU executes the program.

## Components

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

### 62. cpu clock

```txt
clock in:
    | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10| 11| 12| 13| 14| 15| 16| 17| 18| 19| 20| 21| 22| 23| 24| 25| 26| ..
    |___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|
    |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
        ┌───┐   ┌───┐   ┌───┐   ┌───┐   ┌───┐   ┌───┐   ┌───┐   ┌───┐   ┌───┐   ┌───┐   ┌───┐   ┌───┐   ┌───┐   ┌───┐   ┌───┐   ┌───┐
    ────┘   └───┘   └───┘   └───┘   └───┘   └───┘   └───┘   └───┘   └───┘   └───┘   └───┘   └───┘   └───┘   └───┘   └───┘   └───┘   └────

clk:
    | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10| 11| 12| 13| 14| 15| 16| 17| 18| 19| 20| 21| 22| 23| 24| 25| 26| ..
    |___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|
    |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
        ┌───────┐       ┌───────┐       ┌───────┐       ┌───────┐       ┌───────┐       ┌───────┐       ┌───────┐       ┌───────┐       ┌───────┐
    ────┘       └───────┘       └───────┘       └───────┘       └───────┘       └───────┘       └───────┘       └───────┘       └───────┘

clk en:
    | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10| 11| 12| 13| 14| 15| 16| 17| 18| 19| 20| 21| 22| 23| 24| 25| 26| ..
    |___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|
    |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
    ────────────┐   ┌───────────┐   ┌───────────┐   ┌───────────┐   ┌───────────┐   ┌───────────┐   ┌───────────┐
                └───┘           └───┘           └───┘           └───┘           └───┘           └───┘           └───┘           └───┘

clk set:
    | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10| 11| 12| 13| 14| 15| 16| 17| 18| 19| 20| 21| 22| 23| 24| 25| 26| ..
    |___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|___|
    |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
        ┌───┐           ┌───┐           ┌───┐           ┌───┐           ┌───┐           ┌───┐           ┌───┐
    ────┘   └───────────┘   └───────────┘   └───────────┘   └───────────┘   └───────────┘   └───────────┘   └──────────
```

## Instruction Set

1. Register Code
```txt
    r0  - 0000
    r1  - 0001
    r2  - 0010
    r3  - 0011
    r4  - 0100
    r5  - 0101
    r6  - 0110
    r7  - 0111
    r8  - 1000      - stack segment (ss)
    r9  - 1001      - code segment (cs)
    r10 - 1010      - data segment (ds)
    r11 - 1011      - extra segment (es)
    r12 - 1100      - another extra segment (fs) 
    r13 - 1101      - stack pointer (sp)
    r14 - 1110      - flags register (FLAGS) of 16-bit not for arithmetic use, 
                      but for normal manipulations and sometimes serve as temporary register 
                      (TEMP reg) or called 'rr' (reserved register), 
                      which can never be trusted its valud inside it, 
                      usually used as storing transition state for long constructions.
    r15 - 1111      - instruction address register (IAR) of 16-bit (ip)
```

2. Instructions
    The underline (_) is usually considered as 0 for don't care.
    And the data bus bit width is 16 bit.
```txt
    high bits -> low bits
    0000 0000 aaaa bbbb
    @expr
        add ra, rb
    @brief
        ra := ra + rb
    @flow
        0.
        clk en
            enable BUS_1
            load IAR
            ALU := 0000
            sel CS
            set carry
        clk set
            sel MAR
            set ACC
            enable TMP1
            enable carry

        1.
        clk en
            load RAM
        clk set
            store IR

        2.
        clk en
            load ACC
        clk set
            set IAR

        3.
        clk en
            enable CLR
            load CS
            ALU := 1000
        clk set
            set ACC

        4.
        clk en
            load ACC
        clk set
            store CS

        5.
        clk en
            load rb
        clk set
            enable TMP
    
        6.
        clk en
            load ra
            ALU := 0000
        clk set
            set ACC
            set arith FLAGS
    
        7.
        clk en
            load ACC
        clk set
            store ra


    0000 0001 aaaa ____
    ____ ____ ____ xxxx
    @expr
        shr ra, ____ ____ ____ xxxx
    @brief
        But only the lower 4 bits of the second operand used,
        because 'ra' is 16-bit, so maximal need 4-bits to count up to 16.
    @flow
        5.
        clk en
            sel CS
            load IAR

            enable BUS1
            ALU := 0000
            set carry
        clk set
            sel MAR
            set ACC
            enable carry
            enable TMP1

        6.
        clk en
            load ACC
        clk set
            store IAR

        7.
        clk en
            enable CLR
            load CS
            ALU := 1000
        clk set
            set ACC

        8.
        clk en
            load ACC
        clk set
            store CS

        9.
        clk en
            load RAM
        clk set
            enable TMP

        10.
        clk en
            load ra
            ALU := 0001
        clk set
            set ACC
            set arith FLAGS

        11.
        clk en
            load ACC
        clk set
            store ra



    0000 0010 aaaa ____
    ____ ____ ____ xxxx
    @expr
        shl ra, xxxx ____ ____ ____
    @brief
    @flow
        The same flow as shr


    0000 0011 aaaa ____
    @expr
        flip ra
    @brief
    @flow
        5.
        nop

        6.
        clk en
            load ra
            ALU := 0011
        clk set
            set ACC
            set arithmetic FLAGS

        7.
        clk en
            load ACC
        clk set
            store ra


    0000 0100 aaaa bbbb
    @expr
        and ra, rb
    @brief
    @flow
        same as `add ra, rb`


    0000 0101 aaaa bbbb
    @expr
        or ra, rb
    @brief
    @flow
        same as `add ra, rb`


    0000 0110 aaaa bbbb
    @expr
        xor ra, rb
    @brief
    @flow
        same as `add ra, rb`


    0000 0111 aaaa bbbb
    @expr
        cmp ra, rb
    @brief
    @flow
        5.
        clk en
            load rb
        clk set
            enable TMP
    
        6.
        clk en
            load ra
            ALU := 0111
        clk set
            set ACC
            set arithmetic FLAGS
    

    0000 1000 aaaa bbbb
    @expr
        adc ra, rb
    @brief
    @flow
        5.
        clk en
            load rb
            enable arithmetic FLAGS carry
        clk set
            enable TMP
            enable TMP1

        6.
        clk en
            load ra
            ALU := 1000
        clk set
            set ACC
            set arithmetic FLAGS

        7.
        clk en
            load ACC
        clk set
            store ra


    0000 1001 aaaa ____
    ____ ____ ____ xxxx
    @expr
        sar ra, ____ ____ ____ xxxx
    @brief
    @flow
        Same flow as 'shr shl ...'


    0000 1010 aaaa bbbb
    @expr
        subc ra, rb
    @brief
    @flow


    0000 1011 aaaa ____
    @expr
        neg ra
    @brief
    @flow
        5.
        nop

        6.
        clk en
            load ra
            ALU := 1011
        clk set
            set ACC
            set arithmetic FLAGS

        7.
        clk en
            load ACC
        clk set
            store ra


    0000 1100 aaaa bbbb
    @expr
        sub ra, rb
    @brief
        ra := ra - rb
    @flow
        5.
        clk en
            load rb
        clk set
            enable TMP

        6.
        clk en
            load ra
        clk set
            set ACC
            set arithmetic FLAGS

        7.
        clk en
            load ACC
        clk set
            store ra

NOTE:
    here if only the '(arithmetic) carry' flag was set
        
        8.
        clk en
            load ra
            ALU := 0011
        clk set
            set ACC

        9.
        clk en
            load ACC
            enable BUS_1
            ALU := 0000
        clk set
            set ACC

        10.
        clk en
            load ACC
            ALU := 1011
        clk set
            set ACC

        11.
        clk en
            load ACC
        clk set
            store ra


    0000 1101 aaaa bbbb
    @expr
        mul ra, rb
    @brief
    @flow
        The same flow as add ra, rb


    0000 1110 aaaa bbbb
    @expr
        div ra, rb
    @brief
    @flow
        The same flow as add ra, rb

    0000 1111 aaaa bbbb
    @expr
        mod ra, rb
    @brief
    @flow
        The same flow as add ra, rb


    0001 0000 aaaa  ____
    xxxx xxxx xxxx xxxx
    @expr
        mov ra, xxxx xxxx xxxx xxxx
    @example
        mov r0, 0b1111000011110000
        mov r0, 0xf0f0
    @brief
    @flow
        5.
        clk en
            sel CS
            load IAR
            enable BUS_1
            ALU := 0000
            set carry
        clk set
            sel MAR
            set ACC
            enable carry
            enable TMP1
        
        6.
        clk en
            load ACC
        clk set
            set IAR

        7.
        clk en
            enable CLR
            load CS
            ALU := 1000
        clk set
            set ACC

        8.
        clk en
            load ACC
        clk set
            store CS

        9.
        clk en
            load RAM
        clk set
            store ra


    0001 0001 aaaa bbbb
    xxxx xxxx xxxx xxxx
    @expr
        mov ra, byte [rb:xxxx xxxx xxxx xxxx]
    @example
        mov r0, byte [rb:0xf0f0]
    @brief
        This address:
        rb:xxxx xxxx xxxx xxxx 
    @flow
        5.
        clk en
            enable BUS_1
            sel CS
            load IAR
            ALU := 0000
            set carry
        clk set
            sel MAR
            set ACC
            enable carry
            enable TMP1

        6.
        clk en
            load ACC
        clk set
            set IAR

        7.
        clk en
            enable CLR
            load CS
            ALU := 1000
        clk set
            set ACC

        8.
        clk en
            load ACC
        clk set
            store CS

        9.
        clk en
            sel rb
            load RAM
        clk set
            sel MAR

        10.
        clk en
            load RAM
        clk set
            store ra

        11.
        clk en
            load ra
            enable lowmask
            ALU := 0100
        clk set
            set ACC

        12.
        clk en
            load ACC
        clk set
            store ra


    0001 0010 aaaa bbbb
    xxxx xxxx xxxx xxxx
    @expr
        mov ra, word [rb:xxxx xxxx xxxx xxxx]
    @brief
        mov r0, word [0xf0f0]
    @flow
        5.
        clk en
            enable BUS_1
            sel CS
            load IAR
            ALU := 0000
            set carry
        clk set
            sel MAR
            set ACC
            enable carry
            enable TMP1

        6.
        clk en
            load ACC
        clk set
            set IAR

        7.
        clk en
            enable CLR
            load CS
            ALU := 1000
        clk set
            set ACC

        8.
        clk en
            load ACC
        clk set
            store CS

        9.
        clk en
            sel rb
            load RAM
        clk set
            sel MAR

        10.
        clk en
            load RAM
        clk set
            store ra


    0001 0011 aaaa bbbb
    @expr
        mov ra, byte [rb]
    @brief
    @flow
        5.
        clk en
            sel DS
            load rb
        clk set
            sel MAR

        6.
        clk en
            load RAM
        clk set
            store ra

        7.
        clk en
            load ra
            enable lowmask
            ALU := 0100
        clk set
            set ACC

        8.
        clk en
            load ACC
        clk set
            store ra


    0001 0100 aaaa bbbb
    @expr
        mov ra, word [rb]
    @brief
        ds:rb
    @flow
        5.
        clk en
            sel DS
            load rb
        clk set
            sel MAR

        6.
        clk en
            load RAM
        clk set
            store ra


    0001 0101 aaaa bbbb
    @expr
        xchg ra, rb
    @brief
    @flow
        5.
        clk en
            load rb
            enable CLR
            ALU := 0000
        clk set
            set ACC

        6.
        clk en
            load ra
        clk set
            store rb

        7.
        clk en
            load ACC
        clk set
            store ra


    0001 0110 aaaa bbbb
    @expr
        mov ra, rb
    @brief
    @flow
        5.
        clk en
            load rb
        clk set
            store ra

    0001 0111 aaaa bbbb
    xxxx xxxx xxxx xxxx
    @expr
        mov word [ra:rb], imm16
        mov [ra:rb], imm16
    @brief
    @flow
        5.
        clk en
            sel CS
            load IAR
            enable BUS_1
            ALU := 0000
            set carry
        clk set
            sel MAR
            set ACC
            enable carry
            enable TMP1

        6.
        clk en
            load ACC
        clk set
            set IAR

        7.
        clk en
            load CS
            enable CLR
            ALU := 1000
        clk set
            set ACC

        8.
        clk en
            load ACC
        clk set
            store CS

        9.
        clk en
            load RAM
            enable CLR
            ALU := 0000
        clk set
            set ACC

        10.
        clk en
            sel ra
            load rb
        clk set
            sel MAR

        11.
        clk en
            load ACC
        clk set
            store RAM

    0001 1000 aaaa bbbb
    @expr
        mov word [ds:ra], rb
        mov [ds:ra], rb
    @brief
    @flow
        5.
        clk en
            sel DS
            load ra
        clk set
            sel MAR

        6.
        clk en
            load rb
        clk set
            store RAM

    0001 1001 xxxx xxxx
    @expr
    @brief
    @flow

    0001 1010 xxxx xxxx
    @expr
    @brief
    @flow

    0001 1011 xxxx xxxx
    @expr
    @brief
    @flow

    0001 1100 xxxx xxxx
    @expr
    @brief
    @flow

    0001 1101 xxxx xxxx
    @expr
    @brief
    @flow

    0001 1110 xxxx xxxx
    @expr
    @brief
    @flow

    0001 1111 xxxx xxxx
    @expr
    @brief
    @flow

    0010 0000 xxxx xxxx
    @expr
    @brief
    @flow


    0010 0001 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        jmp ra:xxxx xxxx xxxx xxxx
    @brief
        The value of the lower 8-bit inside 'ra' will be the new CS value.
    @flow
        5.
        clk en
            sel CS
            load IAR
        clk set
            sel MAR

        6.
        clk en
            load RAM
        clk set
            set IAR

        7.
        clk en
            load ra
        clk set
            store CS


    0010 0010 aaaa bbbb
    @expr
        jmp ra:rb
    @brief
    @flow
        5.
        clk en
            load ra
        clk set
            store CS

        6.
        clk en
            load rb
        clk set 
            set IAR



NOTE:
    The conditional jump operations looks exactly as their corresponding `jmp` equivalence,
    however, just remember to check for the FLAGS register before jump.

    0010 0011 xxxx xxxx
    @expr
    @brief
    @flow

    0010 0100 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        ja ra:xxxx xxxx xxxx xxxx
    @brief
    @flow

    0010 0101 aaaa bbbb
    @expr
        ja ra:rb
    @brief
    @flow


    0010 0110 xxxx xxxx
    @expr
    @brief
    @flow

    0010 0111 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        jna ra:xxxx xxxx xxxx xxxx
    @brief
    @flow

    0010 1000 aaaa bbbb
    @expr
        jna ra:rb
    @brief
    @flow

    0010 1001 xxxx xxxx
    @expr
    @brief
    @flow

    0010 1010 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        jb ra:xxxx xxxx xxxx xxxx
    @brief
    @flow

    0010 1011 aaaa bbbb
    @expr
        jb ra:rb
    @brief
    @flow

    0010 1100 ____ ____
    xxxx xxxx xxxx xxxx
    @expr
    @brief
    @flow

    0010 1101 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        jnb ra:xxxx xxxx xxxx xxxx
    @brief
    @flow

    0010 1110 aaaa bbbb
    @expr
        jnb ra:rb
    @brief
    @flow

    0010 1111 yyyy yyyy
    @expr
    @brief
    @flow

    0011 0000 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        jeq ra:xxxx xxxx xxxx xxxx
    @brief
    @flow

    0011 0001 aaaa bbbb
    @expr
        jeq ra:rb
    @brief
    @flow

    0011 0010 yyyy yyyy
    @expr
    @brief
    @flow

    0011 0011 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        jneq ra:xxxx xxxx xxxx xxxx
    @brief
    @flow

    0011 0100 aaaa bbbb
    @expr
        jneq ra:rb
    @brief
    @flow

    0011 0101 yyyy yyyy
    @expr
    @brief
    @flow

    0011 0110 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        jc ra:xxxx xxxx xxxx xxxx
    @brief
    @flow

    0011 0111 aaaa bbbb
    @expr
        jc ra:rb
    @brief
    @flow

    0011 1000 yyyy yyyy
    @expr
    @brief
    @flow

    0011 1001 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        jnc ra:xxxx xxxx xxxx xxxx
    @brief
    @flow

    0011 1010 aaaa bbbb
    @expr
        jnc ra:rb
    @brief
    @flow

    0011 1011 yyyy yyyy
    @expr
    @brief
    @flow

    0011 1100 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        jev aaaa:xxxx xxxx xxxx xxxx
    @brief
    @flow
    
    0011 1101 aaaa bbbb
    @expr
        jev ra:rb
    @brief
    @flow

    0011 1110 yyyy yyyy
    @expr
    @brief
    @flow

    0011 1111 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        jnev ra:xxxx xxxx xxxx xxxx
    @brief
    @flow

    0100 0000 aaaa bbbb
    @expr
        jnev ra:rb
    @brief
    @flow

    0100 0001 yyyy yyyy
    @expr
    @brief
    @flow

    0100 0010 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        jp ra:xxxx xxxx xxxx xxxx
    @brief
    @flow

    0100 0011 aaaa bbbb
    @expr
        jp ra:rb
    @brief
    @flow

    0100 0100 yyyy yyyy
    @expr
    @brief
        jump not positive (if positive bit was not set)
    @flow

    0100 0101 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        jnp ra:xxxx xxxx xxxx xxxx
    @brief
    @flow

    0100 0110 aaaa bbbb
    @expr
        jnp ra:rb
    @brief
    @flow

    0100 0111 yyyy yyyy
    @expr
    @brief
    @flow

    0100 1000 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        jz ra:xxxx xxxx xxxx xxxx
    @brief
    @flow

    0100 1001 aaaa bbbb
    @expr
        jz ra:rb
    @brief
    @flow

    0100 1010 yyyy yyyy
    @expr
    @brief
    @flow

    0100 1011 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        jnz ra:xxxx xxxx xxxx xxxx
    @brief
    @flow

    0100 1100 aaaa bbbb
    @expr
        jnz ra:rb
    @brief
    @flow

    0100 1101 yyyy yyyy
    @expr
    @brief
    @flow

    0100 1110 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        jr ra:xxxx xxxx xxxx xxxx
    @brief
    @flow

    0100 1111 aaaa bbbb
    @expr
        jr ra:rb
    @brief
    @flow

    0101 0000 yyyy yyyy
    @expr
    @brief
        jump if 'reserved' bit was not set.
    @flow

    0101 0001 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        jnr ra:xxxx xxxx xxxx xxxx
    @brief
    @flow

    0101 0010 aaaa bbbb
    @expr
        jnr ra:rb
    @brief
    @flow

    0101 0011 yyyy yyyy
    xxxx xxxx xxxx xxxx
    @expr
        call yyyy:xxxx xxxx xxxx xxxx
    @brief
        push IAR
    @flow

    @expr
        call ra:xxxx xxxx xxxx xxxx
    @brief
        push cs
        push ip
        push IAR
        jmp aaaa:xxxx xxxx xxxx xxxx
    @flow

    @expr
        call ra:rb
    @brief
        push IAR
        jmp ra:rb
    @flow

    @expr
        ret
    @brief
        jmp ss:sp
        pop0
    @flow
    ...

    1000 0000 aaaa ____
    @expr
        push ra
    @brief
    @flow
        5.
        clk en
            load sp
            enable BUS_1
            ALU := 0000
            set carry
        clk set
            set ACC
            enable carry
            enable TMP1

        6.
        clk en
            load ACC
        clk set
            store sp

        7.
        clk en
            load SS
            set CLR
            ALU := 1000
        clk set
            set ACC

        8.
        clk en
            load ACC
        clk set
            store SS

        9.
        clk en
            sel SS
            load sp
        clk set
            sel MAR

        10.
        clk en
            load ra
        clk set
            store RAM


    1000 0001 aaaa ____
    @expr
        pop ra
    @brief
    @flow
        5.
        clk en
            sel SS
            load sp
            enable BUS_1
            ALU := 1100
            set carry
        clk set
            sel MAR
            set ACC
            enable carry
            enable TMP1

        6.
        clk en
            load ACC
        clk set
            store sp

        7.
        clk en
            load SS
            enable CLR
            ALU := 1010
        clk set
            set ACC

        8.
        clk en
            load ACC
        clk set
            store SS

        9.
        clk en
            load RAM
        clk set
            store ra


    1000 0010 ____ ____
    xxxx xxxx xxxx xxxx
    @expr
        push xxxx xxxx xxxx xxxx
    @brief
    @flow
        5.
        clk en
            enable BUS_1
            load sp
            ALU := 0000
            enable FLAGS carry
        clk set
            set ACC
            set FLAGS
            enable TMP1

        6.
        clk en
            load ACC
        clk set
            store sp

        7.
        clk en
            set CLR
            load SS
            ALU := 1000
        clk set
            set ACC

        8.
        clk en
            load ACC
        clk set
            store SS

        9.
        clk en
            sel CS
            load IAR
            enable BUS_1
            ALU := 0000
            set carry
        clk set
            sel MAR
            set ACC
            enable carry
            set TMP1

        10.
        clk en
            load ACC
        clk set
            store IAR

        11.
        clk en
            load CS
            enable CLR
            ALU := 1000
        clk set
            set ACC

        12.
        clk en
            load ACC
        clk set
            store CS

        13.
        clk en
            load RAM
            enable CLR
            ALU := 0000
        clk set
            set ACC

        14.
        clk en
            sel SS
            load SP
        clk set
            sel MAR

        15.
        clk en
            load ACC
        clk set
            store RAM


    1000 0011 aaaa bbbb
    @expr
        push byte [ra:rb]
    @brief
    @flow
        5.
        clk en
            load sp
            enable BUS_1
            ALU := 0000
            set carry
        clk set
            set ACC
            enable carry
            enable TMP1

        6.
        clk en
            load ACC
        clk set
            store sp

        7.
        clk en
            set CLR
            load SS
            ALU := 1000
        clk set
            set ACC

        8.
        clk en
            load ACC
        clk set
            store SS

        9.
        clk en
            sel ra
            load rb
        clk set
            sel MAR

        10.
        clk en
            load RAM
            enable lowmask
            ALU := 0100
        clk set
            set ACC

        11.
        clk en
            sel SS
            load sp
        clk set
            sel MAR

        12.
        clk en
            load ACC
        clk set
            store RAM


    1000 0100 aaaa bbbb
    @expr
        push word [ra:rb]
    @brief
    @flow
        5.
        clk en
            load sp
            enable BUS_1
            ALU := 0000
            set carry
        clk set
            set ACC
            enable carry
            enable TMP1

        6.
        clk en
            load ACC
        clk set
            store sp

        7.
        clk en
            set CLR
            load SS
            ALU := 1000
        clk set
            set ACC

        8.
        clk en
            load ACC
        clk set
            store SS

        9.
        clk en
            sel ra
            load rb
        clk set
            sel MAR

        10.
        clk en
            load RAM
            enable CLR
            ALU := 0000
        clk set
            set ACC

        11.
        clk en
            sel SS
            load sp
        clk set
            sel MAR

        12.
        clk en
            load ACC
        clk set
            store RAM



    1000 0101 ____ ____
    xxxx xxxx xxxx xxxx
    @expr
    @brief
    @flow


    1000 0110 ____ ____
    xxxx xxxx xxxx xxxx
    @expr
    @brief
    @flow


    1000 0111 ____ ____
    xxxx xxxx xxxx xxxx
    @expr
    @brief
    @flow

    1000 1000 ____ ____
    xxxx xxxx xxxx xxxx
    @expr
    @brief
    @flow


    1000 1001 aaaa bbbb
    @expr
        pop byte [ra:rb]
    @brief
    @flow
        5.
        clk en
            sel ss
            load sp
            enable BUS_1
            ALU := 1100
            set carry
        clk set
            sel MAR
            set ACC
            enable carry
            enable TMP1

        6.
        clk en
            load ACC
        clk set
            store sp

        7.
        clk en
            load SS
            enable CLR
            ALU := 1010
        clk set
            set ACC

        8.
        clk en
            load ACC
        clk set
            store SS

        9.
        clk en
            load RAM
            enable lowmask
            ALU := 0100
        clk set
            set ACC

        10.
        clk en
            sel ra
            load rb
        clk set
            sel MAR

        11.
        clk en
            load ACC
        clk set
            store RAM


    1000 1010 aaaa bbbb
    @expr
        pop word [ra:rb]
    @brief
    @flow
        5.
        clk en
            sel ss
            load sp
            enable BUS_1
            ALU := 1100
            set carry
        clk set
            sel MAR
            set ACC
            enable carry
            enable TMP1

        6.
        clk en
            load ACC
        clk set
            store sp

        7.
        clk en
            load SS
            enable CLR
            ALU := 1010
        clk set
            set ACC

        8.
        clk en
            load ACC
        clk set
            store SS
        
        9.
        clk en
            load RAM
            enable CLR
            ALU := 0000
        clk set
            set ACC
        
        10.
        clk en
            sel ra
            load rb
        clk set
            sel MAR
        
        11.
        clk en
            load ACC
        clk set
            store RAM


    1000 1011 0000 0000
    @expr
        pop0
    @brief
    @flow
        5.
        clk en
            load sp
            enable BUS_1
            ALU := 1100
            set carry
        clk set
            set ACC
            enable carry
            enable TMP1

        6.
        clk en
            load ACC
        clk set
            store sp

        7.
        clk en
            load SS
            enable CLR
            ALU := 1010
        clk set
            set ACC

        8.
        clk en
            load ACC
        clk set
            store SS

    ...

    1010 0000 aaaa bbbb
    @expr
        add ra, byte [rb]
    @brief
    @flow
        5.
        clk en
            sel ds
            load rb
        clk set
            sel MAR

        6.
        clk en
            load RAM
            enable lowmask
            ALU := 0100
        clk set
            set ACC

        7.
        clk en
            load ACC
        clk set
            enable TMP

        8.
        clk en
            load ra
            ALU := 0000
        clk set
            set ACC
            set arith flags

        9.
        clk en
            load ACC
        clk set
            store ra


    1011 0000 aaaa bbbb
    @expr
        add ra, word [rb]
    @brief
    @flow
        5.
        clk en
            sel ds
            load rb
        clk set
            sel MAR

        6.
        clk en
            load RAM
        clk set
            enable TMP

        7.
        clk en
            load ra
            ALU := 0000
        clk set
            set ACC
            set arith flag

        8.
        clk en
            load ACC
        clk set
            store ra


    1011 0001 aaaa bbbb
    ____ ____ ____ xxxx
    @expr
        shr word [ra:rb], imm4
        shr [ra:rb], imm4
    @brief
    @flow
        5.
        clk en
            sel CS
            load IAR
            enable BUS_1
            ALU := 0000
            set carry
        clk set
            sel MAR
            set ACC
            enable carry
            enable TMP1

        6.
        clk en
            load ACC
        clk set
            store IAR

        7.
        clk en
            load CS
            enable CLR
            ALU := 1000
        clk set
            set ACC

        8.
        clk en
            load ACC
        clk set
            set CS

        9.
        clk en
            load RAM
        clk set
            enable TMP

        10.
        clk en
            sel ra
            load rb
        clk set
            sel MAR

        11.
        clk en
            load RAM
            ALU := 0001
        clk set
            set ACC
            set arithmetic flags

        12.
        clk en
            load ACC
        clk set
            store RAM

    
    1011 0010 aaaa bbbb
    ____ ____ ____ xxxx
    @expr
        shl word [ra:rb], imm4
        shl [ra:rb], imm4
    @brief
    @flow


    1011 0011 aaaa bbbb
    @expr
        flip word [ra:rb]
        flip [ra:rb]
    @brief
    @flow
        5.
        clk en
            sel ra
            load rb
        clk set
            sel MAR

        6.
        clk en
            load RAM
            ALU := 0011
        clk set
            set ACC
            set arith flags

        7.
        clk en
            load ACC
        clk set
            store RAM


    1011 0100 aaaa bbbb
    @expr
        and ra, [ds:rb]
        and ra, [rb]
        and ra, word [ds:rb]
        and ra, word [rb]
    @brief
    @flow


    1011 0101 aaaa bbbb
    @expr
        or ra, [ds:rb]
        or ra, [rb]
        or ra, word [ds:rb]
        or ra, word [rb]
    @brief
    @flow


    1011 0110 aaaa bbbb
    @expr
        xor ra, [ds:rb]
        xor ra, [rb]
        xor ra, word [ds:rb]
        xor ra, word [rb]
    @brief
    @flow

    1011 0111 aaaa bbbb
    @expr
        cmp ra, [ds:rb]
        cmp ra, [rb]
        cmp ra, word [ds:rb]
        cmp ra, word [rb]
    @brief
    @flow


    1011 1000 aaaa bbbb
    @expr
        adc ra, [ds:rb]
        adc ra, [rb]
        adc ra, word [ds:rb]
        adc ra, word [rb]
    @brief
    @flow


    1011 1001 aaaa bbbb
    xxxx ____ ____ ____
    @expr
        sar word [ra:rb], ____ ____ ____ xxxx
    @brief
    @flow


    1011 1011 aaaa bbbb
    @expr
        neg word [ra:rb]
        neg [ra:rb]
    @brief
    @flow


    1011 1101 aaaa bbbb
    @expr
        mul ra, [ds:rb]
        mul ra, [rb]
        mul ra, word [ds:rb]
        mul ra, word [rb]
    @brief
    @flow


    1011 1110 aaaa bbbb
    @expr
        div ra, [ds:rb]
        div ra, [rb]
        div ra, word [ds:rb]
        div ra, word [rb]
    @brief
    @flow


    1011 1111 aaaa bbbb
    @expr
        mod ra, [ds:rb]
        mod ra, [rb]
        mod ra, word [ds:rb]
        mod ra, word [rb]
    @brief
    @flow


    1100 0000 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        add ra, xxxx xxxx xxxx xxxx
    @brief
    @flow
        5.
        clk en
            sel CS
            load IAR
            ALU := 0000
            enable BUS_1
            set carry
        clk set
            sel MAR
            set ACC
            enable carry
            enable TMP1

        6.
        clk en
            load ACC
        clk set
            set IAR

        7.
        clk en
            load CS
            enable CLR
            ALU := 1000
        clk set
            set ACC

        8.
        clk en
            load ACC
        clk set
            store CS

        9.
        clk en
            load RAM
        clk set
            set TMP

        10.
        clk en
            load ra
            ALU := 0000
        clk set
            set ACC
            set arithmetic flags

        11.
        clk en
            load ACC
        clk set
            store ra


    1100 0100 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        and ra, imm16
    @brief
    @flow

    1100 0101 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        or ra, imm16
    @brief
    @flow

    1100 0110 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        xor ra, imm16
    @brief
    @flow

    1100 0111 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        cmp ra, imm16
    @brief
    @flow

    1100 1000 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        adc ra, imm16
    @brief
    @flow

    1100 1100 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        sub ra, imm16
    @brief
    @flow

    1100 1101 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        mul ra, imm16
    @brief
    @flow

    1100 1110 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        div ra, imm16
    @brief
    @flow

    1100 1111 aaaa ____
    xxxx xxxx xxxx xxxx
    @expr
        mod ra, imm16
    @brief
    @flow

    
    1101 0000 aaaa bbbb
    @expr
        add word [ra], rb
    @brief
    @flow
        5.
        clk en
            sel DS
            load ra
        clk set
            sel MAR

        6.
        clk en
            load RAM
        clk set
            enable TMP

        7.
        clk en
            load rb
            ALU := 0000
        clk set
            set ACC
            set arithmetic flags

        8.
        clk en
            load ACC
        clk set
            store RAM


    1110 0000 aaaa bbbb
    xxxx xxxx xxxx xxxx
    @expr
        add word [ra:rb], xxxx xxxx xxxx xxxx
    @brief
    @flow
        5.
        clk en
            sel CS
            load IAR
            enable BUS_1
            ALU := 0000
            set carry
        clk set
            sel MAR
            set ACC
            enable carry
            enable TMP1

        6.
        clk en
            load ACC
        clk set
            set IAR

        7.
        clk en
            load CS
            enable CLR
            ALU := 1000
        clk set
            set ACC

        8.
        clk en
            load ACC
        clk set
            store CS

        9.
        clk en
            load RAM
        clk set
            enable TMP

        10.
        clk en
            sel ra
            load rb
        clk set
            sel MAR

        11.
        clk en
            load RAM
            ALU := 0000
        clk set
            set ACC
            set arithmetic FLAGS

        12.
        clk en
            load ACC
        clk set
            store RAM

    
    1110 0100 aaaa bbbb
    xxxx xxxx xxxx xxxx
    @expr
        and word [ra:rb], imm16
    @brief
    @flow

    1110 0101 aaaa bbbb
    xxxx xxxx xxxx xxxx
    @expr
        or word [ra:rb], imm16
    @brief
    @flow

    1110 0110 aaaa bbbb
    xxxx xxxx xxxx xxxx
    @expr
        xor word [ra:rb], imm16
    @brief
    @flow

    1110 0111 aaaa bbbb
    xxxx xxxx xxxx xxxx
    @expr
        cmp word [ra:rb], imm16
    @brief
    @flow

    ...

    @expr
    @brief
    @flow

    1111 1110 ____ ____
    @expr
        nop
    @brief
    @flow
        5.
        nop

    1111 1111 ____ ____
    @expr
        END
    @brief
    @flow
```

## Demonstration Video
- To open the file *cpu.cir* with the application ***Logisim***. Which is a free software written in Java.
- [demo](https://youtu.be/sKxlbndWQQM)

## Contributing

Contributions are welcome! If you would like to contribute to the project, please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes.
4. Commit your changes (`git commit -m 'Add some feature'`).
5. Push to the branch (`git push origin feature-branch`).
6. Create a new Pull Request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.
















