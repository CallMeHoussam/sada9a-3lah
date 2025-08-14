
## 📌 General Rules (from the subject)

* Submit only the required files in the correct folder names.
* Allowed function: `write` only.
* Compilation flags: `-Wall -Wextra -Werror` — any warning is treated as an error.
* Output must match **exactly** (spaces, commas, newlines).
  Use `./a.out | cat -e` to visualize hidden characters.
* Norminette check: `norminette -R CheckForbiddenSourceHeader`.
* You don’t submit `main()` unless the subject asks for a full program.
* No extra files in your directory.

---

## 🛠 Quick `write()` reminder

```c
ssize_t write(int fd, const void *buf, size_t count);
```

* **fd**: 1 = stdout, 2 = stderr.
* Returns the number of bytes written, or -1 on error.
* Needs a **memory address** for `buf` (`&c` for a single char).
* Doesn’t automatically add `\0` or newline.

---

## 🔡 ASCII quick list

* `'0'..'9'` = 48..57
* `'A'..'Z'` = 65..90
* `'a'..'z'` = 97..122
* char to digit: `c - '0'`
* digit to char: `d + '0'`

---

## **ex00 — ft\_putchar**

**You must know:**

* How `write(1, &c, 1)` works for a single character.
* Difference between `'a'` (char) and `"a"` (string).
* Why `&c` is required (address of the char in memory).

**Defense questions:**

* What is a **file descriptor**? Why is stdout = 1?
* Return type of `write` and handling partial writes.
* Signed vs unsigned `char` and what happens if it’s negative.

**Test ideas:**

* Print spaces, `\n`, symbols, and non-ASCII chars.

---

## **ex01 — ft\_print\_alphabet**

## **ex02 — ft\_print\_reverse\_alphabet**

**You must know:**

* Loop through ASCII from `'a'` to `'z'` (or reverse).
* No newline unless required.
* Order matters.

**Defense questions:**

* Can you do it without a loop (recursion)? What’s the base case?
* How portable is relying on ASCII order?

---

## **ex03 — ft\_print\_numbers**

**You must know:**

* `'0' + i` to print digits in ASCII.
* Difference between int 0 and char `'0'`.

**Defense questions:**

* Why does `'0' + 3` give `'3'`?
* Difference between printing 10 as a number vs two separate characters `'1'` and `'0'`.

---

## **ex04 — ft\_is\_negative**

**You must know:**

* Print `'N'` if `n < 0`, `'P'` if `n >= 0`.
* Zero counts as positive here.

**Defense questions:**

* What are the limits of `int`? (`INT_MIN` and `INT_MAX`)
* Difference between `< 0` and `<= 0`.

---

## **ex05 — ft\_print\_comb** (three different digits)

**You must know:**

* `i < j < k` ensures uniqueness and ascending order.
* Format: `"012, 013, ... 789"` with no trailing comma.

**Defense questions:**

* How do you detect the last combination to avoid a trailing comma?
* Why is `987` not printed? (Lexicographic order)
* How many combinations are there? (C(10,3) = 120)

**Tests:**

* Check first: `012, 013, ...`
* Check last: `789` (no comma).

---

## **ex06 — ft\_print\_comb2** (pairs from 00..99)

**You must know:**

* Always print two digits (leading zero).
* `ab < cd` prevents duplicates.
* Format: `"00 01, 00 02, ... 98 99"`

**Defense questions:**

* How to convert int to two chars without printf.
* Why `01 00` is invalid.
* Complexity and loop structure.

**Tests:**

* First: `00 01`
* Last: `98 99` (no comma).

---

## **ex07 — ft\_putnbr**

**You must know:**

* Printing any `int` using division/remainder to get digits.
* Handle negatives with a leading `-`.
* Special case `INT_MIN` (-2147483648) because `-INT_MIN` overflows.

**Defense questions:**

* Why does `-INT_MIN` overflow? (Two's complement)
* Behavior of `/` and `%` with negatives in C (round toward zero).
* Recursion depth (max \~10 calls).

**Tests:**

* `0`, positive, negative, `INT_MIN`, `INT_MAX`.

---

## **ex08 — ft\_print\_combn**

**You must know:**

* Represent combination as an array of `n` strictly increasing digits.
* Stop when array = `[10-n, ..., 9]`.
* Carry logic: increment from the right, then reset the right side.

**Defense questions:**

* Why strictly increasing? (Avoid duplicates)
* Complexity: number of results = C(10, n).
* Recursion vs iteration trade-offs.

**Tests:**

* n=1 → `0..9`
* n=2 → `01, 02, ..., 89`
* n=9 → `012345678, ..., 123456789` (no comma at end)

---

## ❌ Common pitfalls in C00

* Extra/missing spaces, commas, or newlines.
* Forgetting `INT_MIN` handling in `putnbr`.
* Missing leading zero in `comb2`.
* Wrong folder/file name — Moulinette won’t find your file.
* Using forbidden functions (printf, malloc, etc.) = -42.

---

## ✅ Smart testing tips

```bash
# Compile with all warnings as errors
gcc -Wall -Wextra -Werror file.c && ./a.out | cat -e

# Compare with expected output
diff -u expected.txt <(./a.out)

# Try edge cases
# putnbr: 0, 1, -1, 42, -42, 2147483647, -2147483648
# comb2: "00 01", ..., "98 99"
# combn: n=1, n=2, n=9
```

---

If you want, I can now **generate a printable PDF version** of this cheat sheet so you can keep it next to you during the Piscine.
Do you want me to prepare that?
