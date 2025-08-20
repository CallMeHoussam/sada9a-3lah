# 42 Piscine — C 02 (Deep Preparation Guide, in English)

This module is all about **string manipulation in C**, building your own versions of common libc functions.  
Evaluators often ask questions beyond the implementation: **memory safety, ASCII details, pointer arithmetic, edge cases**.  

Each exercise includes:  
- **You must know**  
- **Defense questions**  
- **Tests**  
- **Keywords & Concepts (with explanations)**  

---

## ex00 — ft_strcpy
**You must know:**
- Reimplement `strcpy(dest, src)`.  
- Copies characters from `src` to `dest`, including the terminating `'\0'`.  
- `dest` must have enough allocated space.  

**Defense questions:**
- What happens if `dest` is smaller than `src`? (→ Buffer overflow, undefined behavior).  
- What if `src` and `dest` overlap? (→ Undefined behavior, not safe).  
- Why do strings in C always need `'\0'`?  

**Tests:**
```c
char src[] = "Hello";
char dest[10];
printf("%s\n", ft_strcpy(dest, src)); // Hello

**Keywords & Concepts:**

* **Null-terminated string** → In C, end marked with `'\0'`.
* **Buffer overflow** → Writing past allocated memory causes UB (security risk).
* **Pointer iteration** → Using `*p++` to copy values.
* **Overlapping memory** → Standard `strcpy` does not handle it; use `memmove` for safe overlap.

---

## ex01 — ft\_strncpy

**You must know:**

* Like `strcpy`, but with a limit `n`.
* If `src` < `n`, fills remaining space with `'\0'`.
* If `src` > `n`, no `'\0'` added → potential non-null-terminated string.

**Defense questions:**

* Difference between `strcpy` and `strncpy`?
* Why is `strncpy` considered unsafe sometimes?
* What’s the advantage of padding with `'\0'`?

**Keywords & Concepts:**

* **Padding** → Remaining bytes filled with zeros.
* **Truncation** → If `src` longer than `n`, `dest` may not have `'\0'`.
* **Safer alternatives** → `strlcpy`.

---

## ex02 — ft\_str\_is\_alpha

**You must know:**

* Returns `1` if all characters are alphabetic (A–Z, a–z).
* Returns `1` if string is empty.

**Defense questions:**

* Why is an empty string considered valid?
* What’s the ASCII range for uppercase and lowercase letters?

**Keywords & Concepts:**

* **Validation functions** → Always return boolean-like values.
* **ASCII Ranges**:

  * 'A'–'Z' = 65–90
  * 'a'–'z' = 97–122

---

## ex03 — ft\_str\_is\_numeric

**You must know:**

* Returns `1` if all characters are digits (0–9).
* Empty string returns `1`.

**Defense questions:**

* What’s the ASCII code for `'0'` and `'9'`?
* What’s the difference between `'0'` and integer `0`?

**Keywords & Concepts:**

* **ASCII Digits**: '0'=48 … '9'=57.
* **Character literal vs integer literal**: `'0'` ≠ `0`.

---

## ex04 — ft\_str\_is\_lowercase

**You must know:**

* Checks only lowercase characters (a–z).

**Defense questions:**

* ASCII codes for lowercase letters?
* Empty string result?

---

## ex05 — ft\_str\_is\_uppercase

**You must know:**

* Same idea, but uppercase only (A–Z).

**Defense questions:**

* Why can’t we just use `isalpha()`? (because `isalpha` includes both cases).
* How to convert uppercase → lowercase using ASCII math?

---

## ex06 — ft\_str\_is\_printable

**You must know:**

* Checks if all characters are printable ASCII (32–126).
* Control characters (<32) and DEL (127) are non-printable.

**Defense questions:**

* What are control characters? (tab, newline, bell, etc.).
* Why does C use ASCII 32 as space?

**Keywords & Concepts:**

* **Printable range**: 32–126.
* **Control chars**: <32 (tab, CR, LF, etc.).
* **DEL**: ASCII 127, non-printable.

---

## ex07 — ft\_strupcase

**You must know:**

* Converts lowercase → uppercase.

**Defense questions:**

* What’s the ASCII difference between 'a' and 'A'? (32).
* Why only letters change, not symbols or digits?

**Keywords & Concepts:**

* **Case conversion** → subtract/add 32.
* **Idempotence** → Applying multiple times has no further effect.

---

## ex08 — ft\_strlowcase

**You must know:**

* Converts uppercase → lowercase.

**Defense questions:**

* ASCII math for conversion?

---

## ex09 — ft\_strcapitalize

**You must know:**

* Capitalizes first character of each word.
* Words = alphanumeric sequences.
* Non-alphanumeric → treated as separators.
* Rest of word becomes lowercase.

**Defense questions:**

* How do you define a “word”?
* What if a word starts with a digit?

**Keywords & Concepts:**

* **Word boundary** → separator = non-alphanumeric.
* **Normalization** → enforce consistent style.
* **Alphanumeric check**.

---

## ex10 — ft\_strlcpy

**You must know:**

* Copies up to `size - 1` chars from `src` to `dest`.
* Always null-terminates (if `size > 0`).
* Returns length of `src`.

**Defense questions:**

* Difference `strncpy` vs `strlcpy`?
* Why is `strlcpy` considered safer?
* What happens if `size=0`?

**Keywords & Concepts:**

* **Buffer size awareness**.
* **Return value** → helps detect truncation.
* **Safer copy**.

---

## ex11 — ft\_putstr\_non\_printable

**You must know:**

* Prints string.
* Non-printable chars → replaced by `\xx` (hex, lowercase).
* Uses only `write()`.

**Defense questions:**

* What’s an escape sequence?
* Why use hex representation?
* Difference between lowercase vs uppercase hex?

**Tests:**

```c
ft_putstr_non_printable("Coucou\ntu vas bien ?");
// Expected: Coucou\0atu vas bien ?
```

**Keywords & Concepts:**

* **Hexadecimal encoding** → 0–15 → 0–9a–f.
* **Write system call** → unbuffered.
* **Escape notation**.

---

## ex12 — ft\_print\_memory

**You must know:**

* Print memory dump:

  1. Address.
  2. Hex bytes (16 per line).
  3. Printable chars (non-printable → `.`).

**Defense questions:**

* What’s the difference between an address and the value stored there?
* Why group 16 bytes per line?
* How do you align incomplete lines?

**Keywords & Concepts:**

* **Memory representation** → visualize raw data.
* **Hex dump format**.
* **Pointer arithmetic**.
* **Endianness** → memory byte order (extra tricky question!).

---

# 🧰 Core Concepts for C02

* **ASCII table** → ranges (letters, digits, printable, control).
* **Null-terminated strings** → `'\0'`.
* **Pointer arithmetic** → `ptr++`.
* **Buffer overflows** → common pitfall in string functions.
* **String normalization** → capitalize, case conversion.
* **Hexadecimal representation** → common in debugging.
* **Memory visualization** → hex dumps, addresses.
* **Safety differences** between `strcpy`, `strncpy`, `strlcpy`.
* **Idempotence** in transformations (uppercase twice = same).
* **Undefined Behavior (UB)** → overlapping buffers, missing `\0`.

```