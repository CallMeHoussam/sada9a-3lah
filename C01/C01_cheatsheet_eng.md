# 42 Piscine — C01 Full Preparation Guide

This guide contains everything you need to prepare for C01 exercises at 42:
- **You must know:** core concepts and required understanding.
- **Defense questions:** what peers/Moulinette-style evaluators might ask.
- **Tests:** how to verify your work and edge cases to check.
- **Keywords & Concepts:** technical vocabulary to know for defense.
- Extra tips for passing Norminette and avoiding pitfalls.

---

## General Rules
- Submit only the required files, in the exact directory and filename.
- Allowed functions: mostly none (only `write` in `ft_putstr`).
- Compile with: `gcc -Wall -Wextra -Werror` — treat warnings as errors.
- Output must match exactly (spaces, commas, no extra newline unless required).
- Check hidden characters: `./a.out | cat -e`
- Run Norminette: `norminette -R CheckForbiddenSourceHeader`
- No extra files in your repo. No `main()` unless required.
- Forbidden functions = -42.

---

## ex00 — ft_ft

**You must know:**
- Passing a pointer to a function.
- Using `*` to modify the value at the pointed location.
- `int *nbr` points to an `int`.

**Defense questions:**
- What is a pointer?
- Difference between `*nbr = 42;` and `nbr = 42;`?
- What happens if you pass NULL?

**Tests:**
- Pass an int variable to `ft_ft` and check value changes to 42.

**Keywords & Concepts:**
- Pointer
- Dereferencing
- Indirection Operator (`*`)
- NULL pointer

---

## ex01 — ft_ultimate_ft

**You must know:**
- Pointer to pointer… 9 levels deep.
- Following the chain to modify the original int.

**Defense questions:**
- What is `int *********nbr`?
- Stack memory vs heap memory.
- Is there a practical reason for multiple indirections?

**Tests:**
- Chain 9 pointers to one int, call function, verify value is 42.

**Keywords & Concepts:**
- Multiple Indirection
- Dereferencing Levels
- Memory Address Chaining

---

## ex02 — ft_swap

**You must know:**
- Swapping values using a temporary variable.
- Passing by address to modify both ints.

**Defense questions:**
- Difference between swapping addresses vs values.
- Why a temp variable is needed.

**Tests:**
- Swap positive numbers, negative numbers, same values.

**Keywords & Concepts:**
- Swap Algorithm
- Temporary Storage
- Passing by Reference

---

## ex03 — ft_div_mod

**You must know:**
- Integer division and modulo.
- Storing results in pointers.
- Behavior with negative numbers.

**Defense questions:**
- Behavior of `/` and `%` with negatives in C.
- What happens if b = 0? (undefined behavior)

**Tests:**
- Positive/negative combinations, divisor = 1, divisor = -1.

**Keywords & Concepts:**
- Division Operator `/`
- Modulo Operator `%`
- Undefined Behavior (divide by zero)

---

## ex04 — ft_ultimate_div_mod

**You must know:**
- Similar to ex03 but modifies original variables directly.
- Store quotient in *a and remainder in *b.

**Defense questions:**
- Difference between returning via pointer vs modifying in place.
- Risks of overwriting original values too early (order of operations).

**Tests:**
- Test with same cases as ex03.

**Keywords & Concepts:**
- In-Place Modification
- Data Overwrite Risk
- Order of Operations

---

## ex05 — ft_putstr

**You must know:**
- Printing a null-terminated string with `write`.
- Looping through each char until `\0`.

**Defense questions:**
- Difference between array of char and pointer to char.
- What is `\0`? Why is it needed?
- How does `write` know when to stop?

**Tests:**
- Empty string, normal text, special characters.

**Keywords & Concepts:**
- Null-Terminator (`\0`)
- String Representation in C
- Standard Output

---

## ex06 — ft_strlen

**You must know:**
- Counting chars until `\0`.
- No `strlen()` from `<string.h>`.

**Defense questions:**
- Why is `\0` important in strings?
- Time complexity of `strlen`.

**Tests:**
- Empty string, long string, string with spaces.

**Keywords & Concepts:**
- String Traversal
- Time Complexity O(n)

---

## ex07 — ft_rev_int_tab

**You must know:**
- Reversing an array in place.
- Swapping elements symmetrically.

**Defense questions:**
- Indexing arrays and pointer arithmetic.
- How many swaps are needed? (`size/2`)

**Tests:**
- Even/odd length arrays, size = 1.

**Keywords & Concepts:**
- In-Place Array Reversal
- Symmetric Swap
- Index Calculation

---

## ex08 — ft_sort_int_tab

**You must know:**
- Sorting array ascending.
- Simple algorithms (bubble sort acceptable here).
- Swapping until sorted.

**Defense questions:**
- Time complexity of your sorting algorithm.
- How to detect if array is already sorted.

**Tests:**
- Already sorted, reverse sorted, duplicates, all equal.

**Keywords & Concepts:**
- Bubble Sort (or similar)
- Time Complexity O(n²)
- Stable vs Unstable Sort

---

## Extra Tips
- Always test with edge cases (NULL pointers if applicable, empty strings, arrays of size 0/1).
- Remember integer division truncates toward zero in C.
- `write` doesn’t append `\0` or newline — you control output formatting.
- In pointer exercises, be ready to draw memory diagrams during defense.
