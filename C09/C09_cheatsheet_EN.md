# 42 Piscine — C 09 (Deep Preparation Guide)

This module focuses on **libraries, Makefiles, and string-splitting with dynamic allocation**.  
Expect evaluators to test your knowledge of **archives, compilation rules, and parsing algorithms**.

---

## ex00 — libft
**You must know:**
- Create a static library `libft.a`.  
- Implement functions:  
  - `ft_putchar` (write one char)  
  - `ft_swap` (swap integers)  
  - `ft_putstr` (print string)  
  - `ft_strlen` (string length)  
  - `ft_strcmp` (string comparison).  
- Use a shell script `libft_creator.sh` to compile and archive.  
- Command: `sh libft_creator.sh`.

**Defense questions:**
- What is a static library? Difference vs dynamic library?  
- How do `ar`, `ranlib`, and `gcc -c` work?  
- Why use `write` instead of `printf`?  
- Why `.a` instead of `.so`?  

**Tests:**
```bash
sh libft_creator.sh
ar t libft.a          # list contents
gcc main.c libft.a && ./a.out
````

**Keywords & Concepts:**

* **Static library (`.a`)**.
* **Archiver (`ar rc`)**.
* **Indexing library (`ranlib`)**.
* **Compilation vs linking**.

---

## ex01 — Makefile

**You must know:**

* Automate compilation of `libft.a` using Makefile.
* Sources in `srcs/`, headers in `includes/`.
* Rules required: `all`, `clean`, `fclean`, `re`, `libft.a`.
* Must not recompile unnecessarily.

**Defense questions:**

* What are Makefile rules and targets?
* What’s the difference between `clean` and `fclean`?
* Why use `-Wall -Wextra -Werror`?
* How does `make` know if recompilation is needed?

**Tests:**

```bash
make        # builds libft.a
make clean  # removes .o files
make fclean # removes .o and libft.a
make re     # cleans + rebuilds
```

**Keywords & Concepts:**

* **Makefile rules**.
* **Dependencies**.
* **Phony targets** (`.PHONY`).
* **Incremental compilation**.

---

## ex02 — ft\_split

**You must know:**

* Prototype:

  ```c
  char **ft_split(char *str, char *charset);
  ```
* Split string `str` into words using any char in `charset` as separator.
* Return an array of strings, last element = `NULL`.
* No empty strings allowed.
* Use `malloc` for words and array.

**Algorithm:**

1. Count how many words (scan string, skip separators).
2. Allocate array of `char *` (size = words + 1).
3. For each word:

   * Find start and end.
   * Allocate space + copy.
4. Null-terminate array.
   → **Parsing + dynamic allocation algorithm**.

**Defense questions:**

* How do you detect a separator?
* Why must the last element be NULL?
* How do you prevent memory leaks if allocation fails?
* Complexity of split? (O(n \* m) with charset lookup).
* Difference between `strtok` (C standard lib) and your implementation?

**Tests:**

```c
char **tab = ft_split("Hello,World 42 Piscine!", " ,!");
for (int i = 0; tab[i]; i++)
    printf("[%s]\n", tab[i]);
// Output: [Hello] [World] [42] [Piscine]
```

**Keywords & Concepts:**

* **Dynamic allocation**.
* **Parsing algorithm**.
* **Delimiter set (charset)**.
* **NULL-terminated arrays**.
* **Memory leaks & free()**.

---

# 🧰 Core Algorithms & Concepts for C09

* **Static library creation** (`ar`, `ranlib`).
* **Makefile automation** (dependencies, rules, clean/rebuild).
* **Parsing algorithm for split** (scan, skip, extract).
* **Dynamic allocation strategies**.
* **NULL-termination convention**.
* **Error handling in memory allocation**.
