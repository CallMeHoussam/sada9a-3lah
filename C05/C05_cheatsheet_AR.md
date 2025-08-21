# 1337 Piscine — C 05 

هاد الـmodule كيركز على **mathematical recursion, prime checking, و backtracking (Ten Queens)**.  
فالديفونس غادي يسولوك بزاف على **algorithm complexity, recursion depth, prime theory, و optimization**.  

كل تمرين فيه:  
- **خاصك تعرف**  
- **Algorithm**  
- **Defense questions**  
- **Keywords & Concepts**  

---

## ex00 — ft_iterative_factorial
**خاصك تعرف:**
- factorial بـloop.  
- factorial كيطلع بسرعة بزاف → overflow.  
- convention: `0! = 1`.  

**Algorithm:**  
```

res = 1
for i from 1 to nb:
res \*= i
return res

```
(O(n) iterative algorithm).  

**Defense questions:**
- علاش factorial كيعمل overflow بسرعة؟  
- شنو هو أكبر `n` لي يقدر يتخزن فـint؟  
- علاش كنعتابرو `0! = 1`؟  

**Keywords & Concepts:**
- **factorial growth (n!)**.  
- **overflow**.  
- **iterative multiplication**.  

---

## ex01 — ft_recursive_factorial
**خاصك تعرف:**
- factorial بطريقة recursive.  

**Algorithm:**  
```

fact(n):
if n < 0 return 0
if n == 0 return 1
return n \* fact(n-1)

```
(O(n) recursive algorithm).  

**Defense questions:**
- الفرق بين iterative و recursive factorial؟  
- شنو هو recursion depth limit؟  
- علاش recursion فـC ماشي efficient بحال iteration؟  

**Keywords & Concepts:**
- **recursion base case**.  
- **call stack**.  
- **stack overflow risk**.  

---

## ex02 — ft_iterative_power
**خاصك تعرف:**
- power بـloop.  
- حالات خاصة: `nb^0 = 1`, `0^0 = 1`.  
- negative exponents → خاصنا نرجعو 0 (حيت int division ماشي float).  

**Algorithm:**  
```

res = 1
for i from 1 to power:
res \*= nb
return res

```
(O(power) algorithm).  

**Defense questions:**
- علاش 0^0 = 1 فهاد المشروع؟  
- الفرق بين negative exponents فـintegers و فـfloats؟  

**Keywords & Concepts:**
- **exponentiation**.  
- **edge case 0^0**.  

---

## ex03 — ft_recursive_power
**خاصك تعرف:**
- power بطريقة recursive.  

**Algorithm:**  
```

pow(nb, p):
if p < 0 return 0
if p == 0 return 1
return nb \* pow(nb, p-1)

```
(O(power) recursive).  

**Defense questions:**
- علاش recursion أقل efficient من iteration هنا؟  
- كاين شي optimization؟ (بحال fast exponentiation O(log n)).  

**Keywords & Concepts:**
- **naive recursion**.  
- **exponentiation by squaring**.  

---

## ex04 — ft_fibonacci
**خاصك تعرف:**
- ترجع الـn-th Fibonacci number.  
- definition: F(0)=0, F(1)=1, F(n)=F(n-1)+F(n-2).  

**Algorithm:**  
```

fib(n):
if n < 0 return -1
if n == 0 return 0
if n == 1 return 1
return fib(n-1) + fib(n-2)

```
(Naive recursion → O(2^n)).  

**Defense questions:**
- علاش naive recursion عندها complexity O(2^n)؟  
- شنو هي memoization و كيفاش كتساعد؟  
- فين كيتستعمل Fibonacci فـCS/math؟  

**Keywords & Concepts:**
- **exponential growth**.  
- **dynamic programming**.  
- **golden ratio approximation**.  

---

## ex05 — ft_sqrt
**خاصك تعرف:**
- ترجع integer square root إلا كان perfect square، وإلا ترجع 0.  

**Algorithm (naive):**  
- Loop i=1..nb → إلا i*i == nb → رجع i.  
- إلا ماكاينش → رجع 0. (O(√n)).  

**Alternative algorithm:**  
- binary search بين 1..nb. (O(log n)).  

**Defense questions:**
- علاش مانشيكوش حتى n كامل؟ (بزاف الوقت).  
- شنو هي complexity ديال الحل ديالك؟  
- علاش sqrt مهم فـprime tests؟  

**Keywords & Concepts:**
- **square root test**.  
- **perfect square**.  
- **O(√n) vs O(log n)**.  

---

## ex06 — ft_is_prime
**خاصك تعرف:**
- ترجع 1 إلا كان nb prime، 0 إلا ماشي prime.  
- prime = غير 1 وراسها لي يقسموها.  
- 0 و 1 ماشي prime.  

**Algorithm:**  
- إلا nb <= 1 → ماشي prime.  
- شيك divisors من 2..√nb.  
- إلا لقينا divisor → رجع 0.  
- إلا ماكاينش → رجع 1. (O(√n)).  

**Defense questions:**
- علاش كنشيكو غير حتى √n؟  
- الفرق بين O(n) check و O(√n)؟  
- علاش 0 و 1 ماشي prime؟  

**Keywords & Concepts:**
- **primality test**.  
- **O(√n) complexity**.  
- **prime definition**.  

---

## ex07 — ft_find_next_prime
**خاصك تعرف:**
- تجيب أصغر prime ≥ nb.  

**Algorithm:**  
- while nb ماشي prime → nb++.  
- رجع nb. (كل test O(√n)).  

**Defense questions:**
- علاش كنستعمل ft_is_prime هنا؟  
- واش هاد الحل efficient مع أعداد كبار؟  
- الفرق بين prime test و prime search؟  

**Keywords & Concepts:**
- **prime search**.  
- **worst-case complexity**.  
- **prime distribution**.  

---

## ex08 — ft_ten_queens_puzzle
**خاصك تعرف:**
- تحط 10 queens فـboard 10x10 بلا ما يهاجمو بعضياتهم.  
- queens كيهجمو فـrow, column, diagonals.  
- خاصك تبين جميع solutions وترجع count.  

**Algorithm (Backtracking):**  
1. حط queen فـcolumn 0.  
2. جرب كل row وش safe (ماشي فـrow/diagonal).  
3. إلا safe → زيد للـcolumn لي ورا.  
4. إلا وصلنا solution كامل → طبعو.  
5. Backtrack باش نلقاو حلول آخرين.  

**Complexity:** ~ O(n!). بالنسبـة n=10 ممكنة.  

**Defense questions:**
- شنو هو backtracking؟  
- كيفاش كتشيك diagonals conflict؟ (row diff == col diff).  
- شحال كاين ديال solutions فـ10 queens؟ (7,264).  
- الفرق بين brute-force و backtracking؟  

**Keywords & Concepts:**
- **backtracking algorithm**.  
- **N-Queens problem**.  
- **constraint satisfaction**.  
- **recursive search tree**.  

---

# 🧰 Core Algorithms فـ C05
- **iterative loops** (factorial, power).  
- **recursion basics** (factorial, power, Fibonacci).  
- **naive recursion vs optimization** (memoization, fast exponentiation).  
- **sqrt بالiteration أو binary search**.  
- **primality test O(√n)**.  
- **prime search by iteration**.  
- **backtracking (Ten Queens)**.  