# Homework of week 6

## Chapter 3, P3

*A. Suppose you have the following three 8-bit bytes: 01010011, 01100110,
01110100. What is the 1's complement of the sum of these 8-bit bytes?*

Answer:  
Here is the detailed process of how the checksum is calculated:

```
  01010011
+ 01100110
-----------
0 10111001
+ 01110100
-----------
1 00101101
+ Carry  1
-----------
  00101110
~
-----------
  11010001
```

Hence the desired answer is `11010001`.

*B. Why is it that UDP takes the 1's complement of the sum; that is, why
not just use the sum?*

Answer:  
Why this happened is detaily explained in `RFC 1071`. From it, we could know
that the following 3 reasons driven to the usage of 1's complement.

- Commutative and Associative
- Byte Order Independence
- Parallel Summation

For *Commutative and Associative*, it means that the checksum can be done in
any order, and it can be arbitrarily split into groups.

For *Byte Order Independence*, due to the existence of little-endian machines
(x86, ARM, LoongArch) and big-endian machines (MIPS, PowerPC, SPARC), the
computation of a ordinary sum is platform-dependent. However, the 1's complement
may be calculated in exactly the same way regardless of the byte order
"big-endian" or "little-endian") of the underlaying hardware, which brings
much convenience.

For *Parallel Summation*, 
On machines that have word-sizes that are multiples of 16 bits, it is possible
to develop even more efficient implementations. Because addition is
associative, we do not have to sum the integers in the order they appear in the
message. Instead we can add them in "parallel" by exploiting the larger word size.

To conclude, using the 1's complement of the sum comes with tons of benefits,
comparing to just using the sum.

*Reference: [RFC1071](https://datatracker.ietf.org/doc/html/rfc1071)*

*C. With the 1's complement scheme, how does the receiver detect errors?*

Answer:  
To detect errors, add the 1's complement sum of data and the checksum.
If the result has all its bits `1`s, the data may have no error.
Otherwise, errors must exist.

*D. Is it possible that a 1-bit error will go undetected?*

Answer:  
It is impossible.

*E. How about a 2-bit error?*

Answer:  
The possibility is not zero. Assume that the transmitted data is
`0x000F` and `0x00F0`, but `0x001E` and `0x00E1` was received. Since the
data's 1's complement sum is the same, the error goes undetected.

## Chapter 3, P8

Please see the figure attached below.

![Answer](assets/rdt3.svg)
