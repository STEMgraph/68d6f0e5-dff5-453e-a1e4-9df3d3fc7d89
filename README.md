<!---
{
  "depends_on": ["memory", "encoding", "mapping"],
  "author": "Stephan Bökelmann",
  "first_used": "2025-03-20",
  "keywords": ["type", "datatype", "encoding", "C"]
}
--->

# Datatypes

## 1) Introduction
Storing information within a computing device is commonly done in a sequence of electrical states.  
Electrical components called "cells" are either charged with electrons or discharged, thus representing two distinct states called `on` and `off`, `high` and `low`, or `1` and `0`.  
Each cell stores a binary digit of information, abbreviated as a `bit`.  
Stringing multiple cells together in addressable units of 8-bit gives us the commonly used `byte`.  

<details>
  <summary>Fun Fact</summary>
  A byte does not have to feature 8-bit.  
  Historically, the size of a byte varied across different computer architectures, ranging from 1 to 48 bits.  
  However, the 8-bit byte became a de facto standard with the IBM System/360, which used 8-bit.  
  The term "byte" was coined by Werner Buchholz in 1956 and refers to the smallest addressable unit within a given computer architecture.
</details>

One way to utilize these bit sequences is by merely using them as a counter, going from `0b 0000 0000` = 0 to `0b 1111 1111` = 255.  
But not everything that we want computers to process consists of numbers between 0 and 255.  
Therefore, interpretation schemata are used.  
One such interpretation scheme is the `ASCII` character set.  
This lookup table assigns a Latin character (and a few others) to each state of a 7-bit sequence.  
Examples:
1. `A` translates to `0b 100 0001`
2. `a` translates to `0b 110 0001`
3. `b` translates to `0b 110 0010`
4. `0` translates to `0b 011 0000`

To make them fit regular 8-bit machines, the C programming language added a _padding_ bit in front, making them 8-bit long.  
The set of these is called the `basic execution character set`.  

In addition to characters, our computing devices should also be able to work with numbers.  
Especially in the early ages of computing, engineers were concerned with storing information as densely as possible.  
Trying to encode a number like `102` in ASCII results in a sequence of 3 bytes or 24 bits.  
Since 8-bit are enough to represent 255 different states, this seems unacceptably large.  
Thus, the programming language `ALGOL 60` in 1960 introduced the idea of differentiating between characters and numbers within its source code, leading to the concept of *datatypes*.  

A *datatype* is a template for a compiler on how to encode information into binary data, as well as communicate which operations are permissible and which are not.  

### 1.1) Further Readings and Other Sources
- [Structured Computer Organization](https://www.amazon.de/Structured-Computer-Organization-Andrew-Tanenbaum/dp/0132916525) by Andrew S. Tanenbaum
- [Algorithms and Data Structures](https://www.amazon.de/-/en/Algorithms-Data-Structures-Niklaus-Wirth/dp/0130220051) by Niklaus Wirth

## 2) Tasks
1. **Bit Patterns**: Take a sheet of paper and make a table. Write down the numbers `0`,...,`8` in individual lines of the first column. Write down the ASCII bit pattern of these numbers in the second column. Write down the integer representation of that number in the third column.
2. **Mappings**: Assume you want your machine to compute the sum of two numbers smaller than four. Your computer takes ASCII input and writes ASCII output, and your machine has a 2-bit adder with a 3-bit output. Draw a concatenated mapping diagram from character to ASCII, to integer, to result in integer, to ASCII, and back to character. Repeat the task without mapping ASCII to integer.
3. **K-Map**: Write down the K-Map for a 2*2-bit -> 3-bit adder.
4. **Boolean Function**: Identify the Boolean function from this map and write them down as:
   ```
   Q_0 ( A_1, A_0, B_1, B_0)
   Q_1 ( A_1, A_0, B_1, B_0)
   Q_2 ( A_1, A_0, B_1, B_0)
   ```
5. **Circuit**: Transform the circuit into a network of logic gates.
6. **ASCII-Math**: Repeat tasks 3, 4, and 5 for ASCII without mapping to integer first.

<details>
  <summary>Hint</summary>
  Do not finish task 6. Stop when you think you have understood the point!
</details>

## 3) Questions
1. Why are calculations not handled in ASCII?
2. Why the representation of numbers to humans not handled in integer?
3. How could you encode a decimal number smaller than `1`?
4. How could you deal with characters that are not part of the latin character-set?


## 4) Advice
Choosing the correct datatypes in your programs ensures both performance and correctness!

