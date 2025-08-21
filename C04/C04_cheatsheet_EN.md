# 42 Piscine — C 04 (Deep Preparation Guide)

This module focuses on **basic I/O, string length, number parsing, and base conversion**.  
Besides the implementation, you should understand the **underlying algorithms** used.  

---

## ex00 — ft_strlen
**You must know:**
- Counts the number of characters in a string until `'\0'`.  
- Prototype: `int ft_strlen(char *str);`.  

**Algorithm:**  
- Initialize counter = 0.  
- Loop while `str[i] != '\0'`.  
- Increment counter.  
- Return counter.  
→ **Linear scan algorithm** (O(n)).  

**Defense questions:**
- Why is complexity O(n)?  
- Difference between `sizeof` and `strlen`?  

**Keywords & Concepts:**
- **Null-terminated string**.  
- **Linear scan algorithm**.  

---

## ex01 — ft_putstr
**You must know:**
- Displays string on stdout using `write`.  

**Algorithm:**  
- Use `ft_strlen` (or loop) to get length.  
- Call `write(1, str, len);`.  
→ **Output loop or bulk write**.  

**Defense questions:**
- Why use `write` instead of `printf`?  
- What happens if `str = NULL`?  

**Keywords & Concepts:**
- **System call write()**.  
- **File descriptor**.  

---

## ex02 — ft_putnbr
**You must know:**
- Prints an integer with `write`.  
- Must handle negatives and `INT_MIN`.  

**Algorithm:**  
- If nb < 0 → print '-' and use recursion on `-nb`.  
- Base case: if nb < 10 → print `'0' + nb`.  
- Else: recurse on `nb / 10`, then print last digit (`nb % 10`).  
→ **Recursive number-to-string algorithm**.  

**Defense questions:**
- Why recursion is natural here?  
- Why is `INT_MIN` special?  

**Keywords & Concepts:**
- **Two’s complement**.  
- **Recursive division/modulo algorithm**.  

---

## ex03 — ft_atoi
**You must know:**
- Converts string to integer.  

**Algorithm:**  
1. Skip whitespaces.  
2. Count `+`/`-` → track final sign.  
3. While char is digit:  
   - result = result * 10 + (digit).  
4. Return `sign * result`.  
→ **Parsing algorithm with base-10 accumulation**.  

**Defense questions:**
- What’s the role of `result = result * 10`?  
- How are multiple `-` handled?  

**Keywords & Concepts:**
- **Parsing loop**.  
- **Accumulation formula**: `res = res*10 + digit`.  

---

## ex04 — ft_putnbr_base
**You must know:**
- Prints integer in arbitrary base.  

**Algorithm:**  
1. Validate base string (length ≥ 2, no duplicates, no `+`/`-`).  
2. If nb < 0 → print '-'.  
3. Recursively:  
   - Divide by base length.  
   - Print remainder using base characters.  
→ **Recursive base conversion algorithm**.  

**Defense questions:**
- Why recursion fits base conversion?  
- How do you handle `INT_MIN`?  

**Keywords & Concepts:**
- **Base conversion algorithm**.  
- **Modulo/division recursion**.  

---

## ex05 — ft_atoi_base
**You must know:**
- Converts string to int in arbitrary base.  

**Algorithm:**  
1. Validate base string.  
2. Skip whitespaces.  
3. Count sign (`+`, `-`).  
4. For each char in `str`:  
   - Find index in `base` string.  
   - result = result * base_length + index.  
5. Return `sign * result`.  
→ **Parsing algorithm with arbitrary base accumulation**.  

**Defense questions:**
- How do you map chars → digits?  
- Why do we check for duplicate chars in base?  

**Keywords & Concepts:**
- **Generalized parsing algorithm**.  
- **Char-to-index mapping**.  
- **Invalid base handling**.  

---

# 🧰 Core Algorithms to Master for C04
- **Linear scan (O(n))** → used in `ft_strlen`, `ft_putstr`.  
- **Recursive number printing** → used in `ft_putnbr`, `ft_putnbr_base`.  
- **String parsing with accumulation** → used in `ft_atoi`, `ft_atoi_base`.  
- **Recursive base conversion** → used in `ft_putnbr_base`.  
- **Char-to-digit mapping** → used in `ft_atoi_base`.  

