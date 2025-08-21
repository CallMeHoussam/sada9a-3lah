# 42 Piscine — C 03 (Deep Preparation Guide)

This module trains you to reimplement **comparison, concatenation, and substring functions**.  
Evaluators will test **edge cases, memory handling, ASCII logic, and pointer arithmetic**.  

Each exercise includes:  
- **You must know**  
- **Algorithm**  
- **Defense questions**  
- **Tests**  
- **Keywords & Concepts (with explanations)**  

---

## ex00 — ft_strcmp
**You must know:**
- Reimplement `strcmp(s1, s2)`.  
- Compares strings lexicographically (ASCII order).  

**Algorithm (Lexicographic comparison):**
1. Loop through both strings simultaneously.  
2. If chars differ → return difference `(s1[i] - s2[i])`.  
3. If one ends → shorter string is "smaller".  
4. If identical until `'\0'` → return 0.  
→ **Linear scan O(n)**.  

**Defense questions:**
- What is lexicographic order?  
- Why return ASCII difference instead of -1/0/1?  
- What happens if one string is shorter?  

**Keywords & Concepts:**
- **Lexicographic comparison** → dictionary order.  
- **ASCII codes** → 'a'=97, 'b'=98.  
- **Signed vs unsigned chars** → may affect extended ASCII.  
- **Null-termination check**.  

---

## ex01 — ft_strncmp
**You must know:**
- Like `strcmp` but compares at most `n` characters.  

**Algorithm (Prefix comparison):**
1. Loop until `i < n` and both chars not `'\0'`.  
2. If mismatch → return difference.  
3. If `n` chars equal or one ends → return 0.  
→ **Linear prefix scan O(n)**.  

**Defense questions:**
- When does it stop early?  
- Why is `n` unsigned?  
- What happens if `n=0`?  

**Keywords & Concepts:**
- **Prefix comparison**.  
- **Boundary conditions** (n=0, shorter strings).  
- **Unsigned loop counters**.  

---

## ex02 — ft_strcat
**You must know:**
- Appends `src` to end of `dest`.  

**Algorithm (Concatenation):**
1. Find end of `dest` (scan until `'\0'`).  
2. Copy characters from `src` to `dest`.  
3. Null-terminate `dest`.  
→ **Linear scan + linear copy O(m+n)**.  

**Defense questions:**
- What’s the difference between copy and append?  
- Why is buffer size critical?  

**Keywords & Concepts:**
- **Concatenation**.  
- **Buffer overflow risk**.  
- **Pointer traversal** → move to `'\0'`.  

---

## ex03 — ft_strncat
**You must know:**
- Like `strcat`, but appends at most `nb` chars.  

**Algorithm (Partial concatenation):**
1. Find end of `dest`.  
2. Copy up to `nb` chars from `src`.  
3. Always null-terminate.  
→ **Bounded linear copy O(n+nb)**.  

**Defense questions:**
- Why does it guarantee null-termination?  
- Difference between `strncat` and `strncpy`?  

**Keywords & Concepts:**
- **Safe concatenation** (but still buffer risks).  
- **Partial concatenation**.  
- **Null-termination rules**.  

---

## ex04 — ft_strstr
**You must know:**
- Finds first occurrence of substring `to_find` in `str`.  

**Algorithm (Naive substring search):**
1. Loop through `str`.  
2. At each position, try to match `to_find`.  
3. If full match → return pointer.  
4. If no match → return NULL.  
→ **O(n*m) naive search**.  

**Defense questions:**
- How check empty `to_find`?  
- Why is complexity O(n*m)?  
- Difference between `strstr` and `strchr`?  

**Keywords & Concepts:**
- **Substring search**.  
- **Empty needle case**.  
- **Return pointer to substring**.  
- **Algorithm complexity**.  

---

## ex05 — ft_strlcat
**You must know:**
- Safer concatenation with explicit buffer size.  
- Returns `strlen(dest) + strlen(src)` (intended length).  

**Algorithm (Safe concatenation with size limit):**
1. Find length of `dest` (up to `size`).  
2. If `size <= dest_len` → return `size + src_len` (truncation).  
3. Else → copy as many `src` chars as fit (`size - dest_len - 1`).  
4. Null-terminate.  
→ **Bounded concatenation algorithm O(n+m)**.  

**Defense questions:**
- Difference `strcat` vs `strncat` vs `strlcat`?  
- What does return value mean?  
- What happens if `size <= strlen(dest)`?  

**Keywords & Concepts:**
- **Buffer size awareness**.  
- **Truncation detection**.  
- **Safer string handling**.  
* **Common bug**: forgetting to subtract `strlen(dest)`.

---

# 🧰 Core Concepts for C03

* **String comparison** (`strcmp`, `strncmp`).
* **Concatenation vs safe concatenation** (`strcat`, `strncat`, `strlcat`).
* **Substring search** (`strstr`).
- **Concatenation algorithm** → scan to end, copy, null-terminate. 
* **Lexicographic order** (ASCII-based).
* **Null-termination** rules.
* **Buffer size management** → risks of overflow.
* **Return values** → detect truncation vs success.
* **Pointer arithmetic** → returning `dest` vs returning pointer into string.
* **Algorithmic complexity** → especially in substring search.
* **Undefined Behavior** → overlapping buffers, missing `'\0'`.
- **Partial concatenation with bound** → (`strncat`).  
- **Naive substring search (O(n*m))** → (`strstr`).  
- **Safe concatenation with buffer size** → (`strlcat`).  

# ⚡ Common Defense Traps
- Confusing return values (`strlcat` length vs `strcat` pointer).  
- Forgetting to null-terminate in `strncat`/`strlcat`.  
- Not handling empty strings.  
- Buffer overflow if `dest` too small.  
- Complexity of `strstr` (O(n*m) unless optimized).  

```