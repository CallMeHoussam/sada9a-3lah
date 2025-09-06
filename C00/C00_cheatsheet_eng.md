
---

# 42 Piscine — C 00 (Deep Preparation Guide)

## 📌 General Rules (from the subject)

* Submit only the required files in the correct folder names.
* Allowed function: **`write` only**.
* Compilation flags: `-Wall -Wextra -Werror` — warnings are errors.
* Output must match **exactly** (spaces, commas, newlines). Use `./a.out | cat -e` to visualize hidden characters.
* Norminette: `norminette -R CheckForbiddenSourceHeader`.
* Don’t submit `main()` unless asked.
* No extra files in the directory.

---

## 🛠 Quick `write()` reminder

```c
ssize_t write(int fd, const void *buf, size_t count);
```

* `fd`: 1 = stdout, 2 = stderr.
* Returns number of bytes written or -1 on error.
* `buf` needs an **address** (`&c` for a single char).
* Does not add `\0` or newline automatically.

---

## 🔡 ASCII quick list

* `'0'..'9'` = 48..57
* `'A'..'Z'` = 65..90
* `'a'..'z'` = 97..122
* char → digit: `c - '0'`
* digit → char: `d + '0'`

---

---

## **ex00 — ft\_putchar**

### You must know

* How to call `write(1, &c, 1)` correctly.
* Why `&c` (address) is required — `write` needs a pointer to the buffer.
* Difference between char literal `'a'` and string literal `"a"`.
* `write` returns `ssize_t` — checkable, but for these exercises you normally ignore the return (still know it exists).

### Tests

* `ft_putchar('a');` → `a`
* `ft_putchar('\n');` → newline (use `cat -e` to verify `$`).
* Print space `' '`, symbol `'#'`, or extended char (observe behavior).

### Algorithms

* Single step: call `write(1, &c, 1);`.

### Defense questions (what they might ask)

* Q: What is a file descriptor?
  A: Integer handle for I/O (`0` stdin, `1` stdout, `2` stderr).
* Q: Why `write` and not `printf`?
  A: Subject forbids stdio; `write` is a low-level system call allowed.
* Q: What happens if `write` returns -1?
  A: An error occurred (e.g., EFAULT or EPIPE); you should know `ssize_t` can be checked.

### Keywords & Concepts

* File descriptor, stdout, system call, buffer, `ssize_t`, address-of (`&`).

### Words you must know

`fd`, `stdout`, `write`, `buffer`, `ssize_t`

### Extra / Pitfalls / Tips

* Don’t call `write(1, c, 1)` — must pass address.
* Keep implementation one-liner, allow Norm compliance (one function, simple).

---

## **ex01 — ft\_print\_alphabet**

### You must know

* How to iterate through letters `'a'`..`'z'`.
* `'a' + i` or `for (char c = 'a'; c <= 'z'; c++)`.
* No newline is required unless the subject asks (check exact output).

### Tests

* Output exactly `abcdefghijklmnopqrstuvwxyz` (verify with `cat -e`).
* Try both `for` and `while` versions; both are acceptable.

### Algorithms

* Simple loop incrementing char:

```c
char c = 'a';
while (c <= 'z') {
  write(1, &c, 1);
  c++;
}
```

### Defense questions

* Q: Could you do this with recursion?
  A: Yes — recursion base case at `'z'`. But iterative is simpler and clearer.
* Q: Are we assuming ASCII? Is that safe?
  A: Piscine problems assume ASCII ordering for these exercises.

### Keywords & Concepts

ASCII, iteration, loop, lexicographic order, character encoding.

### Words you must know

`ASCII`, `iteration`, `loop`, `lexicographic`

### Extra / Pitfalls / Tips

* Don’t print an extra newline unless required.
* Using `int` loop variable is fine — char is OK too.

---

## **ex02 — ft\_print\_reverse\_alphabet**

### You must know

* How to iterate backward from `'z'` to `'a'`.
* Decrementing a char is valid (`c--`).
* Pay attention to loop boundary (`>= 'a'`).

### Tests

* Output exactly `zyxwvutsrqponmlkjihgfedcba`.

### Algorithms

* Reverse loop:

```c
char c = 'z';
while (c >= 'a') {
  write(1, &c, 1);
  c--;
}
```

### Defense questions

* Q: Does signed/unsigned char matter here?
  A: Usually no when comparing to `'a'`/`'z'`, but using `int` avoids sign surprises.
* Q: Could recursion be used?
  A: Yes — but iteration is straightforward.

### Keywords & Concepts

`reverse iteration`, `character set`, `portability`.

### Words you must know

`reverse`, `decrement`, `boundary`

### Extra / Pitfalls / Tips

* Use `int` or `char` consistently; avoid weird behavior if `char` is signed on your platform.

---

## **ex03 — ft\_print\_numbers**

### You must know

* Difference between number `0` and char `'0'`.
* How to compute char for digit: `'0' + i` (where `i` is 0..9).
* Off-by-one errors on loop bounds.

### Tests

* Output exactly `0123456789`.
* Try negative logic accidentally — ensure digits only from `'0'` to `'9'`.

### Algorithms

* Loop `for (char c = '0'; c <= '9'; c++) write(1, &c, 1);`.

### Defense questions

* Q: Why `'0' + 3` equals `'3'`?
  A: Because ASCII codes for digits are contiguous; adding offset shifts to the character code.
* Q: What’s the type of `'0'`?
  A: `int` literal of character constant in C; commonly stored in `char` variables.

### Keywords & Concepts

`ASCII arithmetic`, `character literal`, `integer literal`, `off-by-one`.

### Words you must know

`digit`, `'0'`, `ASCII offset`, `off-by-one`

### Extra / Pitfalls / Tips

* Do not use `printf` or other forbidden functions. Use char arithmetic only.

---

## **ex04 — ft\_is\_negative**

### You must know

* The rule: print `'N'` if `n < 0`, else `'P'`. Zero → `'P'`.
* Correct comparison operator: use `< 0`, not `<= 0`.

### Tests

* `ft_is_negative(-1)` → `N`
* `ft_is_negative(0)`  → `P`
* `ft_is_negative(42)` → `P`

### Algorithms

* `if (n < 0) write(1, "N", 1); else write(1, "P", 1);`

### Defense questions

* Q: What are `INT_MIN` and `INT_MAX`?
  A: The lower and upper bounds of `int`; typical values are -2147483648 and 2147483647 on 32-bit. (Know them conceptually; explain two’s complement.)
* Q: Is 0 negative?
  A: No — per subject rule, 0 prints `P`.

### Keywords & Concepts

`conditional`, `signed integer`, `sign bit`, `integer range`.

### Words you must know

`signed`, `sign`, `INT_MIN`, `INT_MAX`, `comparison`

### Extra / Pitfalls / Tips

* Make sure you don't print extra newline.
* Avoid using `puts`/`printf`.

---

## **ex05 — ft\_print\_comb** (three different digits)

### You must know

* Must print all strictly increasing triplets of digits `i < j < k`, using digits `0..9`.
* Output format: `012, 013, 014, ... 789` — separators are `, `, last combo has no trailing separator.
* Number of combinations = C(10,3) = 120 (good to quote).

### Tests

* First group: `012, 013, 014` — check first outputs.
* Last output: `789` with **no trailing comma**.
* Random checks: ensure `009`, `022`, `111` are **not** printed.

### Algorithms

**Iterative (simple and recommended):**

```c
for (char i = '0'; i <= '7'; i++)
  for (char j = i + 1; j <= '8'; j++)
    for (char k = j + 1; k <= '9'; k++) {
      write three chars i j k;
      if not last (i!='7'||j!='8'||k!='9') write ", ";
    }
```

**Alternative:** generate all permutations and filter `i<j<k` (slower, unnecessary).

### Defense questions

* Q: Why is `987` not printed while `789` is?
  A: The output must be lexicographic ascending sequences of three different digits; `987` is descending.
* Q: How do you avoid trailing comma?
  A: Either detect the last triple `(7,8,9)` or print the separator **before** every item except the first.
* Q: Complexity?
  A: Triple nested loops; fixed small bounds—constant runtime for this assignment.

### Keywords & Concepts

`combination`, `nested loops`, `strictly increasing`, `lexicographic order`, `trailing separator`.

### Words you must know

`combination`, `nested`, `lexicographic`, `separator`, `C(10,3)`

### Extra / Pitfalls / Tips

* Choose either detect-last or "print-first-then-comma" pattern to avoid trailing separator bugs.
* Use `char` or `int` consistently; `char` arithmetic with `'0'` works well.
* Keep loops bounded to `'7','8','9'` to avoid extra iterations.

---

## **ex06 — ft\_print\_comb2** (pairs from `00`..`99`)

### You must know

* All pairs `(a b)` where `0 <= a < b <= 99`.
* Each number printed as two digits (leading zero required for numbers < 10).
* Format: `00 01, 00 02, ..., 98 99` — separators `, `; last pair `98 99` without trailing comma.

### Tests

* First outputs: `00 01, 00 02`
* Ensure `01 00` is not printed.
* Last output: `98 99` (no trailing comma).
* Check `99 99` or `00 00` not printed.

### Algorithms

**Iterative (recommended):**

```c
for (int a = 0; a <= 98; a++) {
  for (int b = a + 1; b <= 99; b++) {
    print_two_digits(a); write(' ');
    print_two_digits(b);
    if (!(a==98 && b==99)) write(", ");
  }
}
```

**print\_two\_digits(n):**

```c
char tens = '0' + (n / 10);
char units= '0' + (n % 10);
write(1, &tens, 1); write(1, &units, 1);
```

### Defense questions

* Q: How do you print leading zero without `printf`?
  A: Use `n / 10` and `n % 10`, convert to `'0' + digit`.
* Q: Why loop `a` to `98`?
  A: Because second number `b` must be > `a`, so if `a`==99 there’s no valid `b`.

### Keywords & Concepts

`leading zero`, `two-digit formatting`, `pair comparison`, `nested loops`, `integer division/modulo`.

### Words you must know

`leading-zero`, `tens`, `units`, `pair`, `formatting`

### Extra / Pitfalls / Tips

* Avoid printing `, ` after last pair; detect `(98,99)` or do "print-first item no comma" pattern.
* Beware `%` with negative numbers (not used here but good to remember).

---

## **ex07 — ft\_putnbr**

### You must know

* Print any `int` value (including `INT_MIN` and `INT_MAX`) using only `write`.
* Negative numbers: print `'-'` then digits of absolute value.
* **Critical:** `-INT_MIN` overflows for 32-bit `int` because absolute of -2147483648 cannot be represented in `int`. Use `long` or `long long` to safely take absolute value or handle `INT_MIN` special case.

### Tests

* `0` → `0`
* `42` → `42`
* `-42` → `-42`
* `2147483647` → `2147483647`
* `-2147483648` → `-2147483648` (must be correct)
* Try sequences of many digits or boundary cases.

### Algorithms

**Recursive (common and clear):**

```c
void ft_putnbr(int nb) {
  long n = nb;             // cast to long to avoid overflow
  if (n < 0) { write('-',1); n = -n; }
  if (n >= 10) ft_putnbr(n / 10);
  char digit = '0' + (n % 10);
  write(1, &digit, 1);
}
```

**Iterative (buffer then reverse):**

* If nb is negative store sign, make `long n = abs(nb)`.
* Extract digits with `% 10` into an array, then print in reverse order.

### Defense questions

* Q: Why cast to `long`?
  A: To avoid overflow when negating `INT_MIN`.
* Q: What’s behavior of `%` and `/` for negative numbers?
  A: In C99 and later integer division rounds toward zero; remainder has the same sign as dividend. (You can explain using examples: `-13/10 == -1`, `-13 % 10 == -3`.)
* Q: Could you print using `printf`?
  A: Not allowed — subject limits to `write`.

### Keywords & Concepts

`recursion`, `division`, `modulo`, `two's complement`, `integer overflow`, `INT_MIN`, `type casting`.

### Words you must know

`INT_MIN`, `overflow`, `recursion`, `abs`, `two's-complement`

### Extra / Pitfalls / Tips

* **Do not** compute `-nb` when `nb == INT_MIN` unless you use `long`.
* Recursion depth ≤ 10 for 32-bit ints — safely small.
* Avoid printing leading zeros; handle `0` as special base case.

---

## **ex08 — ft\_print\_combn** (generalized n-combinations)

### You must know

* Print all strictly increasing sequences of length `n` using digits `0..9`. `0 < n < 10`.
* Each sequence printed as contiguous digits (e.g., `012`), separated by `, `, with no trailing comma.
* Last sequence is `[10-n, 10-n+1, ..., 9]`. Example: for `n=3`, last is `789`.
* Number of outputs = C(10, n).

### Tests

* `n = 1` → `0, 1, 2, ..., 9`
* `n = 2` → `01, 02, ..., 89`
* `n = 9` → single output `0123456789`
* Verify no duplicates, strictly increasing digits per combination.
* Verify last combination detection (no trailing comma).

### Algorithms

**Recursive backtracking (clear and common):**

```c
void recurse(int idx, int n, int start, int digits[]) {
  if (idx == n) {
    print_digits(digits, n);
    if (!is_last_combination(digits, n)) print(", ");
    return;
  }
  for (int d = start; d <= 9; d++) {
    digits[idx] = d;
    recurse(idx+1, n, d+1, digits);
  }
}

// initial call: recurse(0, n, 0, digits)
```

**Iterative (carry/odometer-like):**

1. Initialize digits\[i] = i for `i = 0..n-1` (first combination).
2. While true:

   * Print digits.
   * Find rightmost position `i` such that `digits[i] < max_digit(i)` where `max_digit(i) = 10 - n + i`.
   * If none, break (we are done).
   * Otherwise `digits[i]++`, then for `j = i+1..n-1` set `digits[j] = digits[j-1] + 1`.

**Why `max_digit(i) = 10 - n + i`?**
Because you must leave enough larger digits to fill remaining positions strictly increasing. Example: n=3, i=0 → max = 7 so you can still place 8 and 9 after it.

### Defense questions

* Q: Why recursion is safe here?
  A: Maximum depth is `n`, and `n <= 9` so stack depth is tiny.
* Q: How do you prove correctness?
  A: The recursion enforces `d0 < d1 < ... < d(n-1)` and iterates digits in ascending order — it generates the lexicographic sequence of combinations.
* Q: Complexity?
  A: Number of printed items = C(10, n); time ≈ O(n \* C(10, n)) because printing each item costs `n`. Memory O(n).

### Keywords & Concepts

`backtracking`, `recursion`, `odometer algorithm`, `carry propagation`, `lexicographic generation`, `C(10,n)`.

### Words you must know

`backtracking`, `odometer`, `lexicographic`, `combination`, `C(10,n)`, `max_digit`

### Extra / Pitfalls / Tips

* Carefully compute `max_digit(i)` to implement iterative carry logic correctly.
* Use `int` array `digits[n]` and print using `'0' + digits[i]`.
* Avoid trailing comma by detecting last combination (`digits[0] == 10-n && digits[1] == 10-n+1 ...`) or using a "print-first-without-comma" approach.
* Recursion variant is easier to reason about; iterative may be faster to implement once you understand carry logic.

---

## ❌ Common pitfalls across C00

* Extra or missing spaces/commas/newlines — Moulinette is strict.
* Using forbidden functions (`printf`, `puts`, `malloc`, etc.) — results in -42.
* Not handling `INT_MIN` in `ft_putnbr`.
* Forgetting leading zero for `ft_print_comb2`.
* Wrong file/folder names (Moulinette won't find your submission).
* Violating Norme formatting (use `norminette` locally).

---

## ✅ Smart testing tips

```bash
# compile and run (one file)
gcc -Wall -Wextra -Werror filename.c && ./a.out | cat -e

# compare to expected output file
diff -u expected.txt <(./a.out)

# run many tests:
# - putnbr: 0, 1, -1, 42, -42, 2147483647, -2147483648
# - comb2: 00 01 ... 98 99 (verify first and last)
# - combn: n=1, n=2, n=9
```
