---
layout: default
title: Bit Masking
# nav_order: 2
parent: Problem-Solving Patterns
grand_parent: Programming
tags: #[DP, Recursion, Optimization]
toc: true
toc_sticky: true
date: 2025-01-01
permalink: /programming/problem-solving-pattern/bitmasking
---

# Bitmask Cpp
{: .no_toc }
{% include post-meta.html %}

---

## Table of contents
{: .no_toc .text-delta }
1. TOC
{:toc}

--- 



#### properties
```cpp
     1) property of XOR i.e for any number x, x^x =0.
```

#### general
```cpp
    // bitwise AND => '&'
        0 , 1 -> 0
        0 , 0 -> 0
        1 , 1 -> 1
        1 , 0 -> 0

    // bitwise OR  => '|'
        0 , 1 -> 1
        0 , 0 -> 0
        1 , 1 -> 1
        1 , 0 -> 1

    // bitwise XOR => '^'  
        0 , 1 -> 1
        0 , 0 -> 0
        1 , 1 -> 0
        1 , 0 -> 1

    // compliment '~'
        0 -> 1
        1 -> 0
    
    1 << n ==> 2^n;

```
#### shift_operators

##### left shift  '<<'
```cpp
    a << 1  =>  a * 2
    a << b  =>  a * 2^b
```

##### right shift  '>>'
```cpp
    a >> 1  =>  a / 2
    a >> b  =>  a / 2^b
```

#### odd___even
- Fast way to check the odd even
```cpp
    // inorder to be odd number it has to have its first bit set 
    // and it we do bitwise AND with 1, odd number will return 1 -> true
    int num = 7 // 1 1 1 
    if (num & 1) {
        // num is odd
    } else {
        // num is even
    }
```

#### count_setbits 
```cpp
    int count_set_bits(int num) {
        int count = 0;
        while(num) {
            num = num & (num - 1);
            count++;
        }
        return count;
    }
```

#### XOR_swap
```cpp
    int a = 5;
    int b = 7;
    a = a ^ b; // (5 ^ 7)       -> 
    b = a ^ b; // (5 ^ 7) ^ (7) -> 5 
    a = a ^ b; // (5 ^ 7) ^ (5) -> 7 
```

#### get__set__unset
- get i'th bit of a number
- set i'th bit of a number
- unset i'th bit of a number
 
``` cpp
    //
    int get_i_bit(int num, int i) {
        int mask = 1 << i;
        return (num & mask) != 0 ? 1 : 0;
    }

    void set_i_bit(int &num, int i) {
        int mask = 1 << i;
        num = num | mask;
    }

    void unset_i_bit(int &num, int i) {
        int mask = ~(1 << i);
        num = num & mask;
    }
```

#### right_most_set_and_unset_bit
- position of right most set and unset bit of any number 

> ##### `setbit` `unsetbit`

```py

                                   _
- if n =  2 --> binary rep "00000010" position is 1
                                  _
- if n =  5 --> binary rep "00000101" position is 2
                                  _
- if n = 17 --> binary rep "00010001" position is 2

- if n = 15 --> binary rep "00001111" position is -1
```

```cpp
    int get_pos_of_right_most_set_bit(int n) {
        return log2(n & -n) + 1;
    }

    get_pos_of_right_most_set_bit(2);  // 1 
    get_pos_of_right_most_set_bit(5);  // 2 
    get_pos_of_right_most_set_bit(16); // 1 
    get_pos_of_right_most_set_bit(17); // 2 
    get_pos_of_right_most_set_bit(15); // -1 
```
```cpp
    int get_pos_of_right_most_unset_bit(int n) {
        if (n == 0)
            return 1;
        
        // if all bits of 'n' are set
        if ((n & (n + 1)) == 0)
            return -1;

        return get_pos_of_right_most_set_bit(~n);
    }

    get_pos_of_right_most_unset_bit(2);  // 2 
    get_pos_of_right_most_unset_bit(5);  // 1 
    get_pos_of_right_most_unset_bit(16); // 1 
    get_pos_of_right_most_unset_bit(17); // 1 
    get_pos_of_right_most_unset_bit(15); // 1 

```