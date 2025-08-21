
# 42 Piscine — C 05 (Deep Preparation Guide)

This module focuses on **mathematical recursion, prime checking, and backtracking (Ten Queens)**.  
Expect defense questions about **algorithm complexity, recursion depth, prime theory, and optimization**.  

Each exercise includes:  
- **You must know**  
- **Algorithm**  
- **Defense questions**  
- **Keywords & Concepts**  

---

## ex00 — ft_iterative_factorial
**You must know:**
- Compute factorial with a loop.  
- Factorial grows very fast → overflow risk.  
- By convention: `0! = 1`.  

**Algorithm:**  
```

res = 1
for i from 1 to nb:
res \*= i
return res

```
(O(n) iterative algorithm).  

**Defense questions:**
- Why does factorial overflow quickly?  
- What is the largest `n` that fits in `int`?  
- Why define `0! = 1`?  

**Keywords & Concepts:**
- **Factorial growth (n!)**.  
- **Overflow**.  
- **Iterative multiplication**.  

---

## ex01 — ft_recursive_factorial
**You must know:**
- Recursive version of factorial.  

**Algorithm:**  
```

fact(n):
if n < 0 return 0
if n == 0 return 1
return n \* fact(n-1)

```
(O(n) recursive algorithm).  

**Defense questions:**
- Difference between iterative and recursive implementation?  
- What is recursion depth limit?  
- Why is recursion less efficient in C?  

**Keywords & Concepts:**
- **Recursion base case**.  
- **Call stack**.  
- **Stack overflow risk**.  

---

## ex02 — ft_iterative_power
**You must know:**
- Compute power with a loop.  
- Special cases: `nb^0 = 1`, `0^0 = 1`.  
- Negative exponents return 0 (integer division not allowed).  

**Algorithm:**  
```

res = 1
for i from 1 to power:
res \*= nb
return res

```
(O(power) algorithm).  

**Defense questions:**
- Why return 1 for 0^0 in this project?  
- Difference between negative exponents in integers vs floats?  

**Keywords & Concepts:**
- **Exponentiation**.  
- **Edge case 0^0**.  

---

## ex03 — ft_recursive_power
**You must know:**
- Recursive power.  

**Algorithm:**  
```

pow(nb, p):
if p < 0 return 0
if p == 0 return 1
return nb \* pow(nb, p-1)

```
(O(power) recursive).  

**Defense questions:**
- Why is recursion less efficient than iteration here?  
- What optimization exists? (fast exponentiation O(log n)).  

**Keywords & Concepts:**
- **Naive recursion**.  
- **Exponentiation by squaring** (faster algorithm).  

---

## ex04 — ft_fibonacci
**You must know:**
- Return n-th Fibonacci number.  
- Definition: F(0)=0, F(1)=1, F(n)=F(n-1)+F(n-2).  

**Algorithm:**  
```

fib(n):
if n < 0 return -1
if n == 0 return 0
if n == 1 return 1
return fib(n-1) + fib(n-2)

```
(Naive recursive → O(2^n)).  

**Defense questions:**
- Why is naive recursion exponential complexity?  
- What is memoization? (optimization).  
- Where is Fibonacci used in CS/math?  

**Keywords & Concepts:**
- **Exponential growth**.  
- **Dynamic programming**.  
- **Golden ratio (approximation)**.  

---

## ex05 — ft_sqrt
**You must know:**
- Return integer square root if perfect square, else 0.  

**Algorithm (naive):**  
- Loop i=1..nb → if i*i == nb → return i.  
- If no match → return 0. (O(√n)).  

**Alternative algorithm:**  
- Binary search between 1..nb. (O(log n)).  

**Defense questions:**
- Why not check all numbers up to n? (too slow).  
- What’s complexity of your solution?  
- Why is sqrt important in primality tests?  

**Keywords & Concepts:**
- **Square root test**.  
- **Perfect square**.  
- **Algorithm complexity O(√n) vs O(log n)**.  

---

## ex06 — ft_is_prime
**You must know:**
- Return 1 if prime, 0 if not.  
- Prime: only divisible by 1 and itself.  
- 0 and 1 are not prime.  

**Algorithm:**  
- If nb <= 1 → not prime.  
- Check divisors from 2..√nb.  
- If divisor found → return 0.  
- Else return 1. (O(√n)).  

**Defense questions:**
- Why check only up to √n?  
- What’s the difference between naive O(n) check and optimized O(√n)?  
- Why are 0 and 1 not prime?  

**Keywords & Concepts:**
- **Primality test**.  
- **Complexity O(√n)**.  
- **Definition of prime numbers**.  

---

## ex07 — ft_find_next_prime
**You must know:**
- Find the smallest prime ≥ nb.  

**Algorithm:**  
- While nb not prime → nb++.  
- Return nb. (Each primality test O(√n)).  

**Defense questions:**
- Why use ft_is_prime here?  
- How efficient is this for large nb?  
- What’s the difference between prime test and prime search?  

**Keywords & Concepts:**
- **Prime search**.  
- **Worst-case time complexity**.  
- **Primes distribution** (gaps between primes).  

---

## ex08 — ft_ten_queens_puzzle
**You must know:**
- Place 10 queens on 10x10 board so none attack each other.  
- Queens attack in row, column, diagonals.  
- Must display all solutions and return count.  

**Algorithm (Backtracking):**  
1. Place queen in column 0.  
2. For each row, check if safe (no same row, no diagonal conflict).  
3. If safe, place queen → recurse to next column.  
4. If full solution found → print it.  
5. Backtrack until all solutions explored.  

**Complexity:** ~ O(n!). For n=10, still feasible.  

**Defense questions:**
- What is backtracking?  
- How do you detect diagonal conflicts? (row diff == col diff).  
- How many solutions exist for 10 queens? (7,264).  
- What’s the complexity of brute-force vs backtracking?  

**Keywords & Concepts:**
- **Backtracking algorithm**.  
- **N-Queens problem** (classic CS).  
- **Constraint satisfaction problem**.  
- **Recursive search tree**.  

---

# 🧰 Core Algorithms for C05
- **Iterative loops** (factorial, power).  
- **Recursion basics** (factorial, power, Fibonacci).  
- **Naive recursion vs optimized (memoization, fast exponentiation)**.  
- **Square root via iteration/binary search**.  
- **Primality test (O(√n))**.  
- **Prime search by iteration**.  
- **Backtracking (Ten Queens)**.  
