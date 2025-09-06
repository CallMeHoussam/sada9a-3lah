# 42 Piscine — C 02 (Deep Preparation Guide)

This module focuses on **string copying, validation checks, case transformations, and memory printing**.  
Expect evaluators to test **pointer arithmetic, ASCII logic, parsing, and memory visualization**.


---

## ex00 — ft_strcpy
**You must know:**
- Reimplement `strcpy`.  
- Copies `src` into `dest`, including `'\0'`.  

**Algorithm:**
```c
i = 0;
while (src[i] != '\0')
    dest[i] = src[i], i++;
dest[i] = '\0';
return dest;
```

**Tests:**

```c
char s1[10]; 
ft_strcpy(s1, "42");
printf("%s\n", s1); // 42
```

**Defense questions:**

* What happens if `dest` is too small?
* Difference between `strcpy` and `memcpy`?
* Why must we copy the null terminator?

**Keywords & Concepts:**

* **Null-terminated strings**.
* **Buffer overflow**.
* **Shallow vs deep copy**.

---

## ex01 — ft\_strncpy

**You must know:**

* Reimplement `strncpy`.
* Copies up to `n` chars, padding with `'\0'` if needed.

**Algorithm:**

```c
for (i = 0; i < n && src[i]; i++) 
    dest[i] = src[i];
while (i < n) dest[i++] = '\0';
```

**Tests:**

```c
char s1[10]; 
ft_strncpy(s1, "Hi", 5);
printf("%s\n", s1); // Hi\0\0\0
```

**Defense questions:**

* What if `n` < strlen(src)?
* Why pad with `\0`?
* Difference with `strcpy`?

**Keywords & Concepts:**

* **Partial copy**.
* **Zero-padding**.
* **Fixed-size buffers**.

---

## ex02 — ft\_str\_is\_alpha

**You must know:**

* Returns 1 if all chars are alphabetic (A–Z, a–z), else 0.
* Empty string → return 1.

**Algorithm:**
Loop over chars, check:

```c
if (!((c >= 'A' && c <= 'Z') || (c >= 'a' && c <= 'z')))
    return 0;
return 1;
```

**Tests:**

```c
printf("%d\n", ft_str_is_alpha("Hello")); // 1
printf("%d\n", ft_str_is_alpha("Hi42"));  // 0
```

**Defense questions:**

* Why return 1 for empty string?
* How ASCII ranges define alpha?

**Keywords & Concepts:**

* **Character classes**.
* **Empty string convention**.
* **ASCII ranges**.

---

## ex03 — ft\_str\_is\_numeric

**You must know:**

* Returns 1 if all chars are digits.

**Algorithm:**

```c
if (c < '0' || c > '9') return 0;
```

**Tests:**

```c
printf("%d\n", ft_str_is_numeric("123")); // 1
printf("%d\n", ft_str_is_numeric("12a")); // 0
```

**Defense questions:**

* What’s ASCII code for '0' and '9'?
* Empty string → why return 1?

**Keywords & Concepts:**

* **Digit validation**.
* **ASCII encoding**.

---

## ex04 — ft\_str\_is\_lowercase

**You must know:**

* Returns 1 if all chars are lowercase.

**Algorithm:**

```c
if (c < 'a' || c > 'z') return 0;
```

**Tests:**

```c
printf("%d\n", ft_str_is_lowercase("hello")); // 1
printf("%d\n", ft_str_is_lowercase("Hi"));    // 0
```

**Defense questions:**

* Why empty string = 1?
* What ASCII range is lowercase?

**Keywords & Concepts:**

* **Lowercase ASCII**.
* **String validation**.

---

## ex05 — ft\_str\_is\_uppercase

**You must know:**

* Returns 1 if all chars are uppercase.

**Algorithm:**
Check `c >= 'A' && c <= 'Z'`.

**Tests:**

```c
printf("%d\n", ft_str_is_uppercase("HELLO")); // 1
printf("%d\n", ft_str_is_uppercase("HeLLo")); // 0
```

**Defense questions:**

* Why define uppercase separately from lowercase?

**Keywords & Concepts:**

* **Uppercase ASCII**.
* **Validation functions**.

---

## ex06 — ft\_str\_is\_printable

**You must know:**

* Printable ASCII range: 32–126.

**Algorithm:**

```c
if (c < 32 || c > 126) return 0;
```

**Tests:**

```c
printf("%d\n", ft_str_is_printable("Hi!")); // 1
printf("%d\n", ft_str_is_printable("Hi\n")); // 0
```

**Defense questions:**

* Why `'\n'` is not printable?
* What is ASCII 127?

**Keywords & Concepts:**

* **Printable ASCII range**.
* **Control characters**.

---

## ex07 — ft\_strupcase

**You must know:**

* Convert lowercase → uppercase in place.

**Algorithm:**

```c
if (c >= 'a' && c <= 'z')
    c -= 32;   // ASCII diff
```

**Tests:**

```c
char s[]="hello";
printf("%s\n", ft_strupcase(s)); // HELLO
```

**Defense questions:**

* Why 32 difference between lower/upper?
* Why return str?

**Keywords & Concepts:**

* **ASCII arithmetic**.
* **In-place modification**.

---

## ex08 — ft\_strlowcase

**You must know:**

* Convert uppercase → lowercase.

**Algorithm:**

```c
if (c >= 'A' && c <= 'Z')
    c += 32;
```

**Tests:**

```c
char s[]="HELLO";
printf("%s\n", ft_strlowcase(s)); // hello
```

**Defense questions:**

* Why ASCII offset = 32?
* Difference between returning str and void?

**Keywords & Concepts:**

* **Case conversion**.
* **Mutability**.

---

## ex09 — ft\_strcapitalize

**You must know:**

* Capitalize first letter of each word.
* Other letters → lowercase.
* Word = sequence of alphanumeric chars.

**Algorithm:**

1. Lowercase all.
2. If first char alnum → uppercase.
3. After non-alnum, next alnum → uppercase.

**Tests:**

```c
char s[]="salut, comment tu vas ? 42mots";
printf("%s\n", ft_strcapitalize(s));
// Salut, Comment Tu Vas ? 42mots
```

**Defense questions:**

* What defines a word?
* How to detect alphanumeric?

**Keywords & Concepts:**

* **Parsing algorithm**.
* **Word boundaries**.
* **ASCII checks**.

---

## ex10 — ft\_strlcpy

**You must know:**

* Reimplement `strlcpy`.
* Copies up to `size-1` chars, null-terminates.
* Returns src length.

**Algorithm:**

```c
len = strlen(src);
if (size > 0) {
    copy up to size-1 chars;
    dest[size-1] = '\0';
}
return len;
```

**Tests:**

```c
char d[5];
printf("%u\n", ft_strlcpy(d,"Hello",5)); // 5
printf("%s\n", d); // Hell
```

**Defense questions:**

* Why return src length?
* What if size=0?

**Keywords & Concepts:**

* **Safe copy**.
* **Truncation detection**.

---

## ex11 — ft\_putstr\_non\_printable

**You must know:**

* Print string.
* Replace non-printable char with `\xx` (hex lowercase).

**Algorithm:**

```c
if (c < 32 || c > 126) {
    write("\\");
    print hex of c;
}
```

**Tests:**

```c
ft_putstr_non_printable("Coucou\ntu vas bien ?");
// Coucou\0atu vas bien ?
```

**Defense questions:**

* Why use hex representation?
* Why lowercase hex?

**Keywords & Concepts:**

* **Hexadecimal formatting**.
* **Write system call**.
* **Non-printable encoding**.

---

## ex12 — ft\_print\_memory

**You must know:**

* Print memory in hex dump format.
* Columns: address, hex values, ASCII chars.
* 16 chars per line.
* Non-printable → dot.

**Algorithm:**

1. Print address (padded hex).
2. Print hex content (grouped by 2).
3. Print ASCII (or dot).
   → Repeat for `size` bytes.

**Tests:**
Use sample from subject.

**Defense questions:**

* Why group by 16 bytes?
* Why use dot for non-printables?
* How to handle size=0?

**Keywords & Concepts:**

* **Hex dump algorithm**.
* **Pointer arithmetic**.
* **ASCII visualization**.

---

# 🧰 Core Concepts for C02

* **Copying algorithms**: strcpy, strncpy, strlcpy.
* **Validation algorithms**: alpha, numeric, lowercase, uppercase, printable.
* **Case conversion**: ASCII offsets.
* **Parsing & capitalization**.
* **Hexadecimal formatting**.
* **Memory printing & visualization**.
* **Common pitfalls**: buffer overflow, truncation, empty strings.

```
