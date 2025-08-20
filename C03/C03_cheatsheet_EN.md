# 42 Piscine — C 03 (Deep Preparation Guide, in English)

This module trains you to reimplement **comparison, concatenation, and substring functions**.  
Evaluators will test **edge cases, memory handling, ASCII logic, and pointer arithmetic**.  

Each exercise includes:  
- **You must know**  
- **Defense questions**  
- **Tests**  
- **Keywords & Concepts (with explanations)**  

---

## ex00 — ft_strcmp
**You must know:**
- Reimplement `strcmp(s1, s2)`.  
- Compares strings lexicographically (ASCII order).  
- Returns:  
  - `0` if equal  
  - `<0` if s1 < s2  
  - `>0` if s1 > s2  

**Defense questions:**
- What is lexicographic order?  
- Why does `strcmp` return the difference of ASCII values, not just -1/0/1?  
- How does ASCII encoding affect comparison?  
- What happens if one string is shorter?  

**Tests:**
```c
printf("%d\n", ft_strcmp("abc", "abc")); // 0
printf("%d\n", ft_strcmp("abc", "abd")); // negative
printf("%d\n", ft_strcmp("abd", "abc")); // positive
````

**Keywords & Concepts:**

* **Lexicographic comparison** → like dictionary order.
* **ASCII codes** → 'a'=97, 'b'=98.
* **Unsigned vs signed chars** → may affect results with extended ASCII.
* **Null-termination check**.

---

## ex01 — ft\_strncmp

**You must know:**

* Like `strcmp` but compares at most `n` characters.
* Stops if `n` chars are compared or a `'\0'` is found.

**Defense questions:**

* When does `strncmp` stop early?
* Why is `n` an unsigned int?
* What happens if `n=0`?

**Tests:**

```c
printf("%d\n", ft_strncmp("abc", "abd", 2)); // 0
printf("%d\n", ft_strncmp("abc", "abd", 3)); // negative
```

**Keywords & Concepts:**

* **Prefix comparison**.
* **Boundary conditions** (`n=0`, shorter strings).
* **Unsigned integers in loops**.

---

## ex02 — ft\_strcat

**You must know:**

* Appends `src` to `dest`.
* Assumes `dest` has enough space.
* Returns `dest`.

**Defense questions:**

* What’s the difference between concatenation and copy?
* Why is buffer size important?
* What happens if `dest` isn’t large enough?

**Tests:**

```c
char dest[20] = "Hello, ";
ft_strcat(dest, "World!");
printf("%s\n", dest); // Hello, World!
```

**Keywords & Concepts:**

* **Concatenation**.
* **Buffer overflow risk**.
* **Pointer traversal** → move to `'\0'`, then append.

---

## ex03 — ft\_strncat

**You must know:**

* Like `strcat`, but appends at most `nb` characters.
* Always null-terminates `dest`.

**Defense questions:**

* Why is null-termination guaranteed?
* Difference between `strncat` and `strncpy`?
* What happens if `nb` is larger than `src` length?

**Tests:**

```c
char dest[20] = "Hello, ";
ft_strncat(dest, "World!!!", 5);
printf("%s\n", dest); // Hello, World
```

**Keywords & Concepts:**

* **Safe concatenation** (but still risky if buffer too small).
* **Partial concatenation**.
* **Null-termination rules**.

---

## ex04 — ft\_strstr

**You must know:**

* Finds first occurrence of substring `to_find` in `str`.
* Returns pointer to start of match or `NULL`.
* If `to_find` is empty → return `str`.

**Defense questions:**

* How do you check if `to_find` is empty?
* What’s the difference between returning `NULL` and `str+index`?
* How is `strstr` different from `strchr`?

**Tests:**

```c
printf("%s\n", ft_strstr("Hello World", "World")); // World
printf("%s\n", ft_strstr("Hello", "")); // Hello
printf("%p\n", ft_strstr("Hello", "42")); // NULL
```

**Keywords & Concepts:**

* **Substring search**.
* **Edge cases** → empty needle, no match.
* **Return pointers**.
* **O(n\*m) complexity** (nested search).

---

## ex05 — ft\_strlcat

**You must know:**

* Safer concatenation (like `strlcpy` but for append).
* Appends `src` to `dest`, up to `size - strlen(dest) - 1`.
* Always null-terminates (if `size > 0`).
* Returns total length it tried to create = `strlen(dest) + strlen(src)`.

**Defense questions:**

* Difference between `strcat`, `strncat`, and `strlcat`?
* What does the return value mean?
* Why is `strlcat` safer than `strncat`?
* What happens if `size <= strlen(dest)`?

**Tests:**

```c
char dest[15] = "Hello";
printf("%u\n", ft_strlcat(dest, " World", 15)); // length of attempted string
printf("%s\n", dest); // Hello World
```

**Keywords & Concepts:**

* **Buffer size awareness**.
* **Truncation detection** via return value.
* **Safety in string functions**.
* **Common bug**: forgetting to subtract `strlen(dest)`.

---

# 🧰 Core Concepts for C03

* **String comparison** (`strcmp`, `strncmp`).
* **Concatenation vs safe concatenation** (`strcat`, `strncat`, `strlcat`).
* **Substring search** (`strstr`).
* **Lexicographic order** (ASCII-based).
* **Null-termination** rules.
* **Buffer size management** → risks of overflow.
* **Return values** → detect truncation vs success.
* **Pointer arithmetic** → returning `dest` vs returning pointer into string.
* **Algorithmic complexity** → especially in substring search.
* **Undefined Behavior** → overlapping buffers, missing `'\0'`.

```