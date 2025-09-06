
# 42 Piscine — C 01 (Deep Preparation Guide)

This module focuses on **pointers, swapping, division/modulo, string functions, and array manipulation**.  
Evaluators will test **your understanding of pointer levels, memory addresses, array traversal, and algorithms like reversing and sorting**.

---

## ex00 — ft_ft
**You must know:**
- Function takes a pointer to int and sets the value to 42.  
- Prototype: `void ft_ft(int *nbr);`  

**Algorithm:**  
```c
*nbr = 42;

**Tests:**

```c
int x = 0;
ft_ft(&x);
printf("%d\n", x); // 42
```

**Defense questions:**

* What is a pointer?
* What does `*nbr = 42;` mean?
* What’s the difference between `nbr` and `*nbr`?

**Keywords & Concepts:**

* **Pointer basics**.
* **Dereferencing**.
* **Memory address vs value**.

---

## ex01 — ft\_ultimate\_ft

**You must know:**

* Takes 9 levels of pointers to int and sets value to 42.
* Prototype: `void ft_ultimate_ft(int *********nbr);`.

**Algorithm:**

```c
*********nbr = 42;
```

**Tests:**

```c
int x = 0;
int *p1 = &x; int **p2 = &p1; ... int *********p9 = &p8;
ft_ultimate_ft(p9);
printf("%d\n", x); // 42
```

**Defense questions:**

* What is a multi-level pointer?
* Why do we need so many `*`?
* When would you need double/triple pointers in real code?

**Keywords & Concepts:**

* **Pointer to pointer (double, triple, …)**.
* **Indirection levels**.
* **Practical use cases (argv, malloc of arrays)**.

---

## ex02 — ft\_swap

**You must know:**

* Swaps the values of two integers using pointers.
* Prototype: `void ft_swap(int *a, int *b);`.

**Algorithm:**

```c
temp = *a;
*a = *b;
*b = temp;
```

**Tests:**

```c
int a=1, b=2;
ft_swap(&a, &b);
printf("%d %d\n", a, b); // 2 1
```

**Defense questions:**

* Why do we pass pointers instead of integers?
* What happens if both pointers point to the same variable?

**Keywords & Concepts:**

* **Swap algorithm**.
* **Call by reference vs call by value**.
* **Temporary variable**.

---

## ex03 — ft\_div\_mod

**You must know:**

* Computes division and modulo of two integers.
* Stores results in pointers.
* Prototype: `void ft_div_mod(int a, int b, int *div, int *mod);`.

**Algorithm:**

```c
*div = a / b;
*mod = a % b;
```

**Tests:**

```c
int d, m;
ft_div_mod(10, 3, &d, &m);
printf("%d %d\n", d, m); // 3 1
```

**Defense questions:**

* Why do we use `/` and `%`?
* What happens if `b = 0`?
* Difference between integer division and float division?

**Keywords & Concepts:**

* **Integer division**.
* **Modulo operator**.
* **Division by zero**.

---

## ex04 — ft\_ultimate\_div\_mod

**You must know:**

* Similar to ex03, but modifies values directly.
* Prototype: `void ft_ultimate_div_mod(int *a, int *b);`.

**Algorithm:**

```c
temp = *a;
*a = *a / *b;
*b = temp % *b;
```

**Tests:**

```c
int a=10, b=3;
ft_ultimate_div_mod(&a, &b);
printf("%d %d\n", a, b); // 3 1
```

**Defense questions:**

* Why do we save original \*a in temp?
* What happens if `*b = 0`?
* Why pass by pointer?

**Keywords & Concepts:**

* **In-place update**.
* **Temporary variable to avoid overwriting**.

---

## ex05 — ft\_putstr

**You must know:**

* Writes a string to stdout using `write`.
* Prototype: `void ft_putstr(char *str);`.

**Algorithm:**

```c
while (str[i] != '\0')
    write(1, &str[i], 1);
```

**Tests:**

```c
ft_putstr("Hello World"); // Hello World
```

**Defense questions:**

* What happens if str = NULL?
* Why use `write` instead of printf?
* How do you know string length?

**Keywords & Concepts:**

* **System call write()**.
* **Null-terminated strings**.
* **ASCII characters**.

---

## ex06 — ft\_strlen

**You must know:**

* Counts length of a string until `'\0'`.
* Prototype: `int ft_strlen(char *str);`.

**Algorithm:**

```c
count = 0;
while (str[count] != '\0')
    count++;
return count;
```

**Tests:**

```c
printf("%d\n", ft_strlen("42")); // 2
printf("%d\n", ft_strlen(""));   // 0
```

**Defense questions:**

* Why is complexity O(n)?
* Difference between `sizeof` and `strlen`?

**Keywords & Concepts:**

* **Linear scan algorithm**.
* **Null terminator**.
* **Difference: compile-time size vs runtime length**.

---

## ex07 — ft\_rev\_int\_tab

**You must know:**

* Reverses an int array in place.
* Prototype: `void ft_rev_int_tab(int *tab, int size);`.

**Algorithm:**

```c
for i=0..size/2:
    swap(tab[i], tab[size-1-i]);
```

**Tests:**

```c
int t[5] = {1,2,3,4,5};
ft_rev_int_tab(t, 5); // [5,4,3,2,1]
```

**Defense questions:**

* What’s the algorithm complexity? (O(n))
* Why swap until size/2 only?
* What happens if size=0 or 1?

**Keywords & Concepts:**

* **In-place reversal**.
* **Symmetry in arrays**.
* **Loop invariants**.

---

## ex08 — ft\_sort\_int\_tab

**You must know:**

* Sorts an array of ints in ascending order.
* Prototype: `void ft_sort_int_tab(int *tab, int size);`.

**Algorithm (Bubble Sort):**

```c
for i=0..size-1:
    for j=0..size-2:
        if tab[j] > tab[j+1]:
            swap(tab[j], tab[j+1]);
```

(O(n²)).

**Tests:**

```c
int t[5] = {5,3,1,4,2};
ft_sort_int_tab(t, 5); // [1,2,3,4,5]
```

**Defense questions:**

* What sorting algorithm did you use?
* What’s its complexity?
* Difference between in-place and out-of-place sorting?
* Name faster sorting algorithms (QuickSort, MergeSort).

**Keywords & Concepts:**

* **Sorting algorithms**.
* **Bubble sort (simple, O(n²))**.
* **Algorithmic complexity**.
* **Stability in sorting**.

---

# 🧰 Core Concepts for C01

* **Pointers & dereferencing** (ex00, ex01, ex02, ex04).
* **Swapping values** (ex02, ex07).
* **Division & modulo** (ex03, ex04).
* **String basics: null termination, linear scan, write()** (ex05, ex06).
* **Array manipulation** (reversal, sorting).
* **Algorithmic complexity** (linear O(n), quadratic O(n²)).

```
