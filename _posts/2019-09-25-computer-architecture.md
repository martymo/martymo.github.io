---
layout: post
title: "A Very Brief Introduction to Computer Architecture for Software Developers"
author: "Martym"
categories: computer
tags: [kotlin]
---
# A Very Brief Introduction to Computer Architecture for Software Developers

## Data Representation

### Bits, Bytes, Words, Double words, and Quad words

- Bit - 1 or 0

- Byte - 8 bits

- Word - 16 bits

- Double word - 32 bits, an integer

- Quad word - 64 bits

## Processing

### The Von Neumann architecture

``` asciidoc
 _______________             ____________      ______________
|       |       |           |            |    |              |
|  ALU  |  CU   |           |   Memory   |    |  I/O device  |
|_______|_______|           |____________|    |______________|
|___Registers___|                  |                  |
        |                          |                  |
________|________I/O BUS___________|__________________|

```

- CU - Controller Unit

- ALU - Arithmetic Logic Unit

- Memory - Stored programs + Data

- I/O Bus - CU controls what data is being sent on the I/O bus and
  which device is being controller


### The Fetch-Execute Cycles

``` kotlin

while(Power is on) {
    Fetch an instruction
    Execute the instruction
}

```

`The program counter` is a register that contains an memory address
from which the next instruction will be fetched. After each Fetch,
the program counter is automatically updated to the next memory
address unless the result of the instruction modifies the value
