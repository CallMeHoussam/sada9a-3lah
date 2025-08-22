# 42 Piscine — C 08 (Deep Preparation Guide)

This module introduces **headers, macros, structures, dynamic allocation with structs, and displaying structured data**.  
Expect evaluators to ask about **C preprocessor, macros vs functions, struct memory layout, and dynamic allocation**.

---

## ex00 — ft.h
**You must know:**
- Create a header file `ft.h`.  
- Must contain prototypes:  
  ```c
  void ft_putchar(char c);
  void ft_swap(int *a, int *b);
  void ft_putstr(char *str);
  int ft_strlen(char *str);
  int ft_strcmp(char *s1, char *s2);


* This exercise ensures you understand how to declare prototypes in a `.h` file.

**Defense questions:**

* Why do we need prototypes in headers?
* Difference between `.h` and `.c` files?
* What happens if we include the same `.h` multiple times? (→ use include guards).

**Tests:**

* Include `ft.h` in a small main and check if it compiles.

**Keywords & Concepts:**

* **Header file**.
* **Function prototypes**.
* **Include guards (`#ifndef / #define / #endif`)**.

---

## ex01 — ft\_boolean.h

**You must know:**

* Define a custom boolean type with macros.
* Must work with a provided main that checks if `argc - 1` is even.
* Define macros: `TRUE`, `FALSE`, `EVEN(nbr)`, `EVEN_MSG`, `ODD_MSG`, `SUCCESS`.

**Defense questions:**

* Why use macros instead of `typedef enum`?
* How does `EVEN(nbr)` macro expand?
* Why do we use `(nbr % 2 == 0)` instead of `(nbr & 1)`?

**Tests:**

* Run program with even and odd number of args.

**Keywords & Concepts:**

* **Macros** (`#define`).
* **Conditional macros**.
* **Boolean type in C** (before `<stdbool.h>`).

---

## ex02 — ft\_abs.h

**You must know:**

* Define a macro `ABS(Value)` returning the absolute value.
* Watch for parentheses: `#define ABS(Value) ((Value) < 0 ? -(Value) : (Value))`.

**Defense questions:**

* Why use parentheses around `Value`?
* Difference between macro vs inline function?
* Possible pitfalls? (e.g., `ABS(x++)` increments twice).

**Tests:**

```c
printf("%d\n", ABS(-42)); // 42
printf("%d\n", ABS(7));   // 7
```

**Keywords & Concepts:**

* **Macro expansion**.
* **Ternary operator**.
* **Side effects with macros**.

---

## ex03 — ft\_point.h

**You must know:**

* Define a struct for a point:

  ```c
  typedef struct s_point {
      int x;
      int y;
  } t_point;
  ```
* Program uses it to store coordinates.

**Defense questions:**

* Difference between `struct` and `typedef struct`?
* How is memory allocated for struct members?
* How do you access members via pointer? (`point->x`).

**Tests:**

* Assign `t_point p; p.x = 42; p.y = 21;`.

**Keywords & Concepts:**

* **Structs**.
* **Arrow operator (`->`) vs dot (`.`)**.
* **Memory layout of structs**.

---

## ex04 — ft\_strs\_to\_tab

**You must know:**

* Create an array of structs from an array of strings.
* Prototype:

  ```c
  struct s_stock_str *ft_strs_to_tab(int ac, char **av);
  ```
* Struct contains:

  * `int size;` (length of string).
  * `char *str;` (original string).
  * `char *copy;` (heap-allocated copy).
* Must allocate memory dynamically, last element’s `str = 0`.

**Defense questions:**

* Why do we need a deep copy of string?
* Difference between shallow copy vs deep copy?
* How to handle allocation failure?
* Why mark the end with `str = 0`?

**Tests:**

* Convert `argv` into stock\_str array and print.

**Keywords & Concepts:**

* **Dynamic allocation (`malloc`, `free`)**.
* **Deep vs shallow copy**.
* **Sentinel value (str = 0)**.

---

## ex05 — ft\_show\_tab

**You must know:**

* Display the struct array created by `ft_strs_to_tab`.
* Print:

  * string + newline
  * size + newline
  * copy + newline
* Must use `write`.

**Defense questions:**

* Why use `write` instead of `printf`?
* How to convert int to string for printing? (→ recursion / iterative).
* What happens if `copy` was modified?

**Tests:**

* Call `ft_show_tab(ft_strs_to_tab(ac, av));`.

**Keywords & Concepts:**

* **Struct traversal**.
* **Printing integers recursively**.
* **Low-level output**.

---

# 🧰 Core Algorithms & Concepts for C08

* **Include guards** (prevent multiple inclusion).
* **Macros vs inline functions** (pros/cons).
* **Ternary operator**.
* **Struct definition & memory layout**.
* **Pointer access with `->`**.
* **Dynamic allocation of struct arrays**.
* **Deep copy vs shallow copy**.
* **Sentinel values** (null termination style).
* **Low-level I/O with write()**.