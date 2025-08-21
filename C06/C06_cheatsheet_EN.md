# 42 Piscine — C 06 (Deep Preparation Guide )

This module teaches you how to **handle command-line arguments (`argc`, `argv`)** and apply simple algorithms like reversing and sorting.  
Expect defense questions about **program execution, argv memory, ASCII sorting, and algorithms complexity**.  

Each exercise includes:  
- **You must know**  
- **Algorithm**  
- **Defense questions**  
- **Keywords & Concepts**  

---

## ex00 — ft_print_program_name
**You must know:**
- Program should print its own name (`argv[0]`).  
- Only `write` is allowed.  

**Algorithm:**  
- Loop over characters in `argv[0]`.  
- Print them one by one using `write`.  
(O(n), linear scan).  

**Defense questions:**
- What does `argv[0]` always contain?  
- Is the program name always `./a.out`? (No, it depends how it was executed).  
- What is the difference between `argc` and `argv`?  

**Keywords & Concepts:**
- **argc** → argument count.  
- **argv** → argument vector (array of strings).  
- **argv[0]** → program name.  
- **Linear scan**.  

---

## ex01 — ft_print_params
**You must know:**
- Print all arguments passed to program, one per line.  
- Skip `argv[0]`.  

**Algorithm:**  
- For i = 1 → argc-1:  
  - Print each `argv[i]` character by character.  
(O(total length of args)).  

**Defense questions:**
- Why skip `argv[0]`?  
- How are arguments separated when you pass them in terminal?  
- What happens if no arguments are passed?  

**Keywords & Concepts:**
- **argv as an array of strings**.  
- **Iteration over argc**.  
- **I/O with write**.  

---

## ex02 — ft_rev_params
**You must know:**
- Print arguments in reverse order.  

**Algorithm:**  
- For i = argc-1 → 1:  
  - Print each `argv[i]`.  
→ Simple reverse loop.  

**Defense questions:**
- What is the difference between reversing characters and reversing arguments?  
- Is reversing always O(n)?  
- What happens if there are no arguments?  

**Keywords & Concepts:**
- **Reverse iteration**.  
- **Indexing in arrays**.  
- **Order of arguments in memory**.  

---

## ex03 — ft_sort_params
**You must know:**
- Sort arguments alphabetically (ASCII order).  
- Print them one per line.  

**Algorithm (Bubble Sort example):**  
```

for i from 1 to argc-1:
for j from i+1 to argc-1:
if strcmp(argv[i], argv[j]) > 0:
swap(argv[i], argv[j])

```
(O(n²) comparison-based sorting).  

**Defense questions:**
- Why ASCII order, not dictionary order?  
- How does `strcmp` work internally?  
- What’s the complexity of bubble sort?  
- Can you use another sorting algorithm here (like quicksort)?  

**Keywords & Concepts:**
- **Sorting algorithms** (Bubble sort, Selection sort).  
- **Lexicographic order** (ASCII-based).  
- **String comparison**.  
- **Pointer swapping**.  

---

# 🧰 Core Algorithms for C06
- **Linear scan** → printing program name, arguments.  
- **Loop iteration** → printing argv elements.  
- **Reverse iteration** → printing argv backwards.  
- **Sorting algorithms** → bubble sort, selection sort (O(n²)).  
- **String comparison (strcmp)** → lexicographic order using ASCII values.  

---

# ⚡ Defense Traps in C06
- Difference between `argv[0]` vs actual arguments.  
- ASCII vs alphabetical order (capital letters before lowercase).  
- Sorting complexity O(n²).  
- Can arguments be empty strings? (yes).  
- What happens with very long arguments? (still works, just longer strings).  
- Why only `write` is allowed? (to force low-level string handling).  