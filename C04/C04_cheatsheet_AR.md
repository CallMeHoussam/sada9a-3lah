
# 1337 Piscine — C 04

هاد الـmodule كيركز على **basic I/O, string length, number parsing, و base conversion**.  
المهم ماشي غير الكود، ولكن تكون عارف **شنو هو الـalgorithm لي ورا كل function**.  

---

## ex00 — ft_strlen
**خاصك تعرف:**
- كتحسب عدد ديال characters فـstring حتى توصل لـ `'\0'`.  
- Prototype: `int ft_strlen(char *str);`.  

**Algorithm:**  
- دير counter = 0.  
- Loop: مادام `str[i] != '\0'` زيد counter++.  
- رجع counter.  
→ **Linear scan (O(n))**.  

**Defense questions:**
- علاش complexity O(n)؟  
- الفرق بين `sizeof` و `strlen`؟  

**Keywords & Concepts:**
- **null-terminated string**.  
- **linear scan algorithm**.  

---

## ex01 — ft_putstr
**خاصك تعرف:**
- كيطبع string على stdout بـ `write`.  

**Algorithm:**  
- يا إما تستعمل `ft_strlen` باش تعرف length.  
- ولا loop حتى `'\0'` وتطبع كل char.  
→ **output loop أو bulk write**.  

**Defense questions:**
- علاش نستعمل `write` وماشي `printf`؟  
- شنو كيوقع إلا str = NULL؟  

**Keywords & Concepts:**
- **system call write()**.  
- **file descriptor**.  

---

## ex02 — ft_putnbr
**خاصك تعرف:**
- كيطبع int بـ `write`.  
- خاصك تعالج negative numbers و `INT_MIN`.  

**Algorithm:**  
- إلا nb < 0 → طبع `'-'` وعاود خدم على `-nb`.  
- Base case: إلا nb < 10 → طبع `'0' + nb`.  
- Else: recursive call على `nb / 10` ومن بعد طبع `nb % 10`.  
→ **recursive number-to-string algorithm**.  

**Defense questions:**
- علاش recursion طبيعي هنا؟  
- علاش `INT_MIN` case خاص؟  

**Keywords & Concepts:**
- **two’s complement**.  
- **recursive division/modulo algorithm**.  

---

## ex03 — ft_atoi
**خاصك تعرف:**
- كتحول string → int.  

**Algorithm:**  
1. Skip whitespaces.  
2. Count signs `+` و `-`.  
3. Loop على digits:  
   - res = res * 10 + digit.  
4. رجع res * sign.  
→ **parsing algorithm بالbase-10 accumulation**.  

**Defense questions:**
- علاش كنستعمل formula res = res*10 + digit؟  
- كفاش كيتعاملو مع بزاف ديال `-`؟  

**Keywords & Concepts:**
- **parsing loop**.  
- **accumulation formula**.  

---

## ex04 — ft_putnbr_base
**خاصك تعرف:**
- كيطبع int بأي base.  

**Algorithm:**  
1. validate base string (طول ≥ 2، بلا duplicates، بلا `+`/`-`).  
2. إلا nb < 0 → طبع `'-'`.  
3. recursion:  
   - nb ÷ base_len  
   - remainder = nb % base_len  
   - طبع base[remainder].  
→ **recursive base conversion algorithm**.  

**Defense questions:**
- علاش recursion كيناسب base conversion؟  
- كيفاش تعالج `INT_MIN`؟  

**Keywords & Concepts:**
- **base conversion algorithm**.  
- **modulo/division recursion**.  

---

## ex05 — ft_atoi_base
**خاصك تعرف:**
- كتحول string → int بأي base.  

**Algorithm:**  
1. validate base string.  
2. Skip whitespaces.  
3. Count signs.  
4. Loop على str:  
   - قلب على index ديال char فـbase.  
   - res = res * base_len + index.  
5. رجع res * sign.  
→ **general parsing algorithm (arbitrary base accumulation)**.  

**Defense questions:**
- كفاش كنديرو mapping بين char → digit؟  
- علاش خاصنا نمنعو duplicate chars فـbase؟  

**Keywords & Concepts:**
- **char-to-index mapping**.  
- **invalid base handling**.  
- **generalized parsing algorithm**.  

---

# 🧰 Core Algorithms خاصين بـ C04
- **linear scan O(n)** → `ft_strlen`, `ft_putstr`.  
- **recursive number printing** → `ft_putnbr`, `ft_putnbr_base`.  
- **string parsing & accumulation** → `ft_atoi`, `ft_atoi_base`.  
- **recursive base conversion** → `ft_putnbr_base`.  
- **char-to-digit mapping** → `ft_atoi_base`.  

---

# ⚡ Defense traps
- الخلط بين `sizeof` و `strlen`.  
- `INT_MIN` special case.  
- ASCII digits vs chars.  
- invalid bases (duplicates أو base_len < 2).  
- multiple signs فـ`ft_atoi`.  