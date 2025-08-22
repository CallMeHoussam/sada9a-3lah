# 42 Piscine — C 07 (Deep Preparation Guide)

This module focuses on **dynamic memory allocation, string manipulation, base conversion, and splitting algorithms**.  
Expect evaluators to ask about **malloc, memory leaks, pointer handling, parsing, and complexity of your algorithms**.

---

## ex00 — ft_strdup
**You must know:**
- Reimplement `strdup`.  
- Allocate memory with `malloc` and copy the string.  
- Remember to add the `'\0'`.  

**Algorithm:**  
1. Measure length of `src`.  
2. Allocate `len + 1` chars.  
3. Copy chars one by one.  
4. Add `'\0'`.  

**Defense questions:**
- What happens if `malloc` fails?  
- Why add `+1` in allocation?  
- Difference between stack string vs heap string?  

**Tests:**
```c
printf("%s\n", ft_strdup("42"));   // 42
printf("%s\n", ft_strdup(""));     // ""
````

**Keywords & Concepts:**

* **malloc/free**.
* **Heap vs stack**.
* **Shallow vs deep copy**.

---

## ex01 — ft\_range

**You must know:**

* Create int array from `min` (inclusive) to `max` (exclusive).
* Return `NULL` if min >= max.

**Algorithm:**

1. If min >= max → return NULL.
2. Allocate `(max - min)` integers.
3. Fill array with values from min to max-1.

**Defense questions:**

* Why return `NULL` for invalid range?
* How much memory do we allocate? (bytes).
* What happens if max-min is huge?

**Tests:**

```c
int *arr = ft_range(3, 6);
printf("%d %d %d\n", arr[0], arr[1], arr[2]); // 3 4 5
```

**Keywords & Concepts:**

* **Array allocation**.
* **Pointer arithmetic**.
* **NULL return convention**.

---

## ex02 — ft\_ultimate\_range

**You must know:**

* Similar to `ft_range`, but takes `int **range`.
* Returns size of range, or 0 if invalid, or -1 if malloc fails.

**Algorithm:**

1. If min >= max → set `*range = NULL`, return 0.
2. Allocate `(max - min)` ints.
3. Fill with values.
4. Return size.

**Defense questions:**

* Why do we use `int **range` instead of return pointer?
* How to detect allocation failure?
* What’s the meaning of return values (0, size, -1)?

**Tests:**

```c
int *arr;
int size = ft_ultimate_range(&arr, 3, 6);
printf("%d\n", size);  // 3
```

**Keywords & Concepts:**

* **Double pointer**.
* **Output parameters**.
* **Error signaling with return codes**.

---

## ex03 — ft\_strjoin

**You must know:**

* Concatenate array of strings (`strs`) with separator (`sep`).
* If size == 0 → return malloc’ed empty string.

**Algorithm:**

1. Calculate total length: sum of all strings + sep\*(size-1).
2. Allocate memory.
3. Copy each string, insert sep in between.

**Defense questions:**

* How do you calculate length before allocation?
* Why must we return an empty malloced string for size=0?
* Risk of buffer overflow?

**Tests:**

```c
char *s[] = {"Hello", "42", "World"};
printf("%s\n", ft_strjoin(3, s, " ")); // Hello 42 World
```

**Keywords & Concepts:**

* **Dynamic concatenation**.
* **Buffer size calculation**.
* **Separator logic**.

---

## ex04 — ft\_convert\_base

**You must know:**

* Convert `nbr` string from base\_from → base\_to.
* Validate base (no duplicates, ≥2 chars, no +/-, no spaces).
* Handle negative numbers.

**Algorithm:**

1. Validate both bases.
2. Parse nbr string into integer (like `ft_atoi_base`).
3. Convert integer into base\_to string (recursion / loop).
4. Return malloc’ed result.

**Defense questions:**

* How do you validate a base string?
* How to handle `INT_MIN`?
* Why use recursion in base conversion?
* What happens if result is “0”?

**Tests:**

```c
printf("%s\n", ft_convert_base("1010", "01", "0123456789")); // 10
```

**Keywords & Concepts:**

* **Base validation**.
* **String parsing**.
* **Recursion for base conversion**.
* **Modulo/division algorithm**.

---

## ex05 — ft\_split

**You must know:**

* Split string `str` using any char in `charset` as separator.
* Return NULL-terminated array of strings.
* No empty strings allowed.

**Algorithm:**

1. Count words (non-separator sequences).
2. Allocate array of char\*.
3. For each word: allocate string, copy chars.
4. End array with NULL.

**Defense questions:**

* How to detect separators vs words?
* Why ensure no empty strings?
* What’s the complexity? (O(n) scan).
* How to free memory on failure?

**Tests:**

```c
char **arr = ft_split("Hello,,42,World", ",");
printf("%s %s %s\n", arr[0], arr[1], arr[2]); // Hello 42 World
```

**Keywords & Concepts:**

* **String tokenization**.
* **Dynamic arrays**.
* **Memory management & leaks**.
* **NULL-terminated arrays**.

---

# 🧰 Core Algorithms for C07

* **Linear scan + malloc copy** → ft\_strdup.
* **Range generation** → ft\_range, ft\_ultimate\_range.
* **Concatenation with pre-calculated size** → ft\_strjoin.
* **Parsing + conversion (atoi\_base + putnbr\_base)** → ft\_convert\_base.
* **Tokenization & word counting** → ft\_split.
* **Validation routines** → base validation, malloc error checks.