# 42 Piscine — C 02 (Deep Preparation Guide with Algorithm Concepts)

This module focuses on **string copy, validation, transformations, and memory visualization**.  
Each exercise is tied to a **fundamental algorithm or concept** that evaluators may expect you to explain.

---

## ex00 — ft_strcpy
**You must know:**
- Copy a string from source to destination until `'\0'`.  

**Algorithm concept:**  
- **Sequential copy algorithm** → scan characters one by one and copy until end marker (null terminator).  

**Defense questions:**
- Why is `null terminator` important?  
- What happens if `dest` is too small?  
- Difference between `strcpy` and memcpy?
- Why must we copy the null terminator?

**Keywords & Concepts:**  
- String copy, buffer overflow, null-terminated string.

---

## ex01 — ft_strncpy
**You must know:**
- Copy at most `n` characters, pad with `'\0'` if needed.  

**Algorithm concept:**  
- **Fixed-length copy algorithm** → copy up to n chars, then fill remaining space with nulls if shorter.  

**Defense questions:**  
- What happens if `n` < length of source?  
- Why is zero-padding needed?  
- Difference with `strcpy`?

**Keywords & Concepts:**  
- Partial copy, buffer padding, safe string handling.

---

## ex02 — ft_str_is_alpha
**You must know:**  
- Check if string contains only alphabetic chars.  

**Algorithm concept:**  
- **Validation scan algorithm** → loop through string, verify each char falls inside ASCII alpha ranges.  

**Defense questions:**  
- Why return 1 for empty string?  
- How ASCII ranges define alpha?

**Keywords & Concepts:**  
- Character classification, ASCII ranges, validation.

---

## ex03 — ft_str_is_numeric
**You must know:**  
- Check if string contains only digits.  

**Algorithm concept:**  
- **Digit validation scan** → check every char between '0'–'9'.  

**Defense questions:**  
- ASCII codes for digits?  
- Why empty string = 1?  

**Keywords & Concepts:**  
- ASCII digits, numeric validation, parsing.

---

## ex04 — ft_str_is_lowercase
**You must know:**  
- Verify all chars are lowercase.  

**Algorithm concept:**  
- **Range check algorithm** → confirm each char in 'a'–'z'.  

**Defense questions:**  
- Why validate ranges instead of checking all letters manually?  

**Keywords & Concepts:**  
- ASCII lowercase,
- validation,
- scanning.

---

## ex05 — ft_str_is_uppercase
**You must know:**  
- Verify all chars are uppercase.  

**Algorithm concept:**  
- **Range check validation** → test every char in 'A'–'Z'.  

**Defense questions:**  
- What happens if string has mixed cases?  
- Why define uppercase separately from lowercase?

**Keywords & Concepts:**  
- Uppercase validation,
- ASCII ranges.

---

## ex06 — ft_str_is_printable
**You must know:**  
- Return 1 if all chars are printable (ASCII 32–126).  

**Algorithm concept:**  
- **Printability validation** → check ASCII code range validity.  

**Defense questions:**  
- Why are newline, tab not printable?  
- What is ASCII 127?  

**Keywords & Concepts:**  
- Printable vs control characters,
- ASCII standard.

---

## ex07 — ft_strupcase
**You must know:**  
- Transform lowercase → uppercase.  

**Algorithm concept:**  
- **Case transformation algorithm** → add/subtract fixed ASCII offset to shift case.  

**Defense questions:**  
- Why ASCII offset = 32?  
- Why return str?

**Keywords & Concepts:**  
- ASCII arithmetic,
- uppercase conversion.

---

## ex08 — ft_strlowcase
**You must know:**  
- Transform uppercase → lowercase.  

**Algorithm concept:**  
- **Case transformation algorithm** → opposite of ex07, apply ASCII offset.  

**Defense questions:**  
- Why modify in place instead of returning new string?  
- Difference between returning str and void?

**Keywords & Concepts:**  
- Case transformation,
- mutability,
- ASCII offset.

---

## ex09 — ft_strcapitalize
**You must know:**  
- Capitalize first letter of each word, lowercase the rest.  

**Algorithm concept:**  
- **Parsing + word-boundary detection** → scan, detect start of word, capitalize first, lowercase following.  

**Defense questions:**  
- What defines a "word"?  
- How do you detect alphanumeric boundaries?  

**Keywords & Concepts:**  
- Tokenization, parsing, capitalization algorithm.

---

## ex10 — ft_strlcpy
**You must know:**  
- Copy safely into fixed buffer size, always null-terminate.  

**Algorithm concept:**  
- **Safe copy with truncation detection** → copy up to `size-1`, track full length of source.  

**Defense questions:**  
- Why return source length?  
- What happens if size = 0?  

**Keywords & Concepts:**  
- Safe string functions, truncation, buffer management.

---

## ex11 — ft_putstr_non_printable
**You must know:**  
- Display string, non-printable chars → hex with `\`.  

**Algorithm concept:**  
- **String formatting with hex encoding** → detect non-printables, transform into hexadecimal escape sequence.  

**Defense questions:**  
- Why hex instead of decimal?  
- Why always 2 digits in hex?  

**Keywords & Concepts:**  
- Hexadecimal representation, escape sequences, non-printables.

---

## ex12 — ft_print_memory
**You must know:**  
- Display memory content with hex + ASCII.  

**Algorithm concept:**  
- **Hex dump algorithm** →  
  1. Print address.  
  2. Print bytes in hex, grouped.  
  3. Print ASCII (dots for non-printables).  

**Defense questions:**  
- Why group memory by 16 bytes?  
- What’s the difference between pointer arithmetic and array indexing?  
- How to handle size=0?

**Keywords & Concepts:**  
- Memory dump, hex formatting, visualization, pointer arithmetic.

---

# 🧰 Core Algorithm Concepts for C02
- **Sequential copy** (strcpy).  
- **Fixed-length copy with padding** (strncpy).  
- **Validation scans** (alpha, digit, printable, case checks).  
- **ASCII-based transformations** (upper/lower conversion).  
- **Parsing with boundaries** (capitalize).  
- **Safe copying with truncation handling** (strlcpy).  
- **Formatting algorithms** (escape hex, hex dump).  
