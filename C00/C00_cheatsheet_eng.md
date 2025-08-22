# 🏊 Piscine C00 — Deep Preparation Guide

---

### **Ex00 – ft\_putchar**

**Goal:** Write a function to display one character using `write`.

* ❓ **Defense Questions**

  * What is the prototype of `write`?
  * Why use `&c` instead of just `c`?
  * What does `1` mean in `write(1, &c, 1)`?

* 🧠 **Algorithm**

  * Take one `char` → pass its **address** to `write`.

* 🔑 **Keywords & Concepts**

  * `write()` system call (unistd.h).
  * File descriptors (`0` stdin, `1` stdout, `2` stderr).
  * Difference between character vs. string.

* 📌 **You must know**

  * ASCII basics.
  * How to compile: `gcc -Wall -Wextra -Werror ft_putchar.c`.

* 🧪 **Tests**

  ```c
  ft_putchar('A'); // should print A
  ft_putchar('z'); // should print z
  ```

---

### **Ex01 – ft\_print\_alphabet**

**Goal:** Print all lowercase letters from `a` to `z`.

* ❓ **Defense Questions**

  * How to loop through characters?
  * Difference between `++` on int and char?

* 🧠 **Algorithm**

  * Initialize `char c = 'a'`.
  * While `c <= 'z'`, print with `write`.

* 🔑 **Keywords & Concepts**

  * ASCII ordering `'a' → 'z'`.
  * While loop.

* 📌 **You must know**

  * Incrementing chars works like ints (`'a'+1 = 'b'`).

* 🧪 **Tests**

  ```
  Output: abcdefghijklmnopqrstuvwxyz
  ```

---

### **Ex02 – ft\_print\_reverse\_alphabet**

**Goal:** Print alphabet from `z` to `a`.

* ❓ **Defense Questions**

  * How to reverse a loop in C?

* 🧠 **Algorithm**

  * Start from `char c = 'z'`.
  * Decrement until `'a'`.

* 🔑 **Keywords & Concepts**

  * Decrement operator `--`.

* 📌 **You must know**

  * Loops can count backwards too.

* 🧪 **Tests**

  ```
  Output: zyxwvutsrqponmlkjihgfedcba
  ```

---

### **Ex03 – ft\_print\_numbers**

**Goal:** Print all digits `0` to `9`.

* ❓ **Defense Questions**

  * ASCII value of `'0'`?
  * Why use chars instead of ints?

* 🧠 **Algorithm**

  * Loop `c = '0'` to `'9'`.

* 🔑 **Keywords & Concepts**

  * ASCII `'0' = 48`.

* 📌 **You must know**

  * `write` expects chars, not ints.

* 🧪 **Tests**

  ```
  Output: 0123456789
  ```

---

### **Ex04 – ft\_is\_negative**

**Goal:** Display `'N'` if negative, `'P'` if positive or zero.

* ❓ **Defense Questions**

  * What is the difference between `>=` and `>`?
  * Why is zero considered positive?

* 🧠 **Algorithm**

  * If `n < 0` → print `'N'`.
  * Else → print `'P'`.

* 🔑 **Keywords & Concepts**

  * Conditional `if / else`.
  * Integers sign.

* 📌 **You must know**

  * `int` range in C (`-2,147,483,648` to `2,147,483,647`).

* 🧪 **Tests**

  ```c
  ft_is_negative(-5); // N
  ft_is_negative(0);  // P
  ft_is_negative(7);  // P
  ```

---

### **Ex05 – ft\_print\_comb**

**Goal:** Print all 3-digit combinations without repetition (012, 013, … 789).

* ❓ **Defense Questions**

  * How do you avoid repetitions like 112 or 221?
  * Why stop at `789`?

* 🧠 **Algorithm**

  * Triple nested loop: `a` from '0' to '7', `b` from a+1, `c` from b+1.
  * Print each with `write`.
  * Add `", "` except last.

* 🔑 **Keywords & Concepts**

  * Nested loops.
  * ASCII logic for digits.

* 📌 **You must know**

  * The **last case check** (avoid trailing comma).

* 🧪 **Tests**

  ```
  Output: 012, 013, ..., 789
  ```

---

### **Ex06 – ft\_print\_comb2**

**Goal:** Print all combinations of two 2-digit numbers from `00 01` to `98 99`.

* ❓ **Defense Questions**

  * Why use `00` instead of `0`?
  * How to separate numbers with space?

* 🧠 **Algorithm**

  * Two nested loops: `i` from 0 to 98, `j` from i+1 to 99.
  * Convert int to 2-digit string with `/` and `%`.
  * Print with space in between.

* 🔑 **Keywords & Concepts**

  * Division (`/`) and modulo (`%`) for digits.
  * Double loop optimization.

* 📌 **You must know**

  * How to pad numbers with leading zero.

* 🧪 **Tests**

  ```
  Output starts: 00 01, 00 02, ..., 98 99
  ```

---

### **Ex07 – ft\_putnbr**

**Goal:** Print any integer (positive or negative).

* ❓ **Defense Questions**

  * How to handle negative numbers?
  * What about `-2147483648`?
  * Why use recursion?

* 🧠 **Algorithm**

  * If `nb == INT_MIN` → special case.
  * If `nb < 0` → print `'-'`, then call recursively with `-nb`.
  * Print digits with recursion: `ft_putnbr(nb/10)` then last digit.

* 🔑 **Keywords & Concepts**

  * Recursion.
  * Integer limits.

* 📌 **You must know**

  * `int` range.
  * How to convert digit → char (`+ '0'`).

* 🧪 **Tests**

  ```c
  ft_putnbr(42);     // 42
  ft_putnbr(-42);    // -42
  ft_putnbr(0);      // 0
  ft_putnbr(-2147483648); // -2147483648
  ```

---

### **Ex08 – ft\_print\_combn**

**Goal:** Print all combinations of `n` digits (0 < n < 10).

* ❓ **Defense Questions**

  * What is recursion / backtracking?
  * How to avoid duplicates?

* 🧠 **Algorithm**

  * Use recursion/backtracking.
  * Ensure strictly increasing order.
  * Print digits, add `", "` except last.

* 🔑 **Keywords & Concepts**

  * Recursion.
  * Backtracking.
  * Generalization of Ex05 & Ex06.

* 📌 **You must know**

  * How to generate combinations systematically.

* 🧪 **Tests**

  ```
  n = 2 → 01, 02, ..., 89
  n = 3 → 012, 013, ..., 789
  n = 9 → 123456789
  ```