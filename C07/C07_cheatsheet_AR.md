# 1337 Piscine — C 07

هاد الموديول ديال C07 كيركز على:  
- **dynamic memory allocation** (malloc, free)  
- **string manipulation** (copy, join)  
- **base conversion** (decimal ↔ binary ↔ hex)  
- **splitting algorithms** (tokenization)  

فالـ defense، غادي يسولوك بزاف على:  
- memory leaks  
- heap vs stack  
- pointer handling  
- recursion  
- parsing & complexity analysis  

---

## ex00 — ft_strdup
**You must know:**  
- تعاود دير `strdup`.  
- تخصك دير malloc باش تخصص memory جديدة فالـ heap.  
- تنسخ الـ string char ب char و تزيد `'\0'` فالآخر.  

**Algorithm (concept):**  
1. تحسب طول `src`.  
2. تخص allocate ديال `len + 1`.  
3. تنسخ chars.  
4. تسالي بـ `'\0'`.  

**Defense questions:**  
- شنو يوقع إلا malloc فشلت؟  
- علاش خاصنا `+1`؟  
- الفرق بين stack string و heap string؟  

**Keywords & Concepts:**  
- malloc/free  
- heap vs stack  
- shallow copy vs deep copy  

---

## ex01 — ft_range
**You must know:**  
- ترجع int array من min حتى max (max excluded).  
- إلا min >= max → return NULL.  

**Algorithm (concept):**  
1. Check: إلا min >= max → NULL.  
2. Allocate `(max - min)` ints.  
3. عمر array بالقيم.  

**Defense questions:**  
- علاش كنرجعو NULL إلا min >= max؟  
- شحال ديال bytes غادي يتخصصو؟  
- شنو يوقع إلا الفرق كبير بزاف؟  

**Keywords & Concepts:**  
- array allocation  
- pointer arithmetic  
- NULL return convention  

---

## ex02 — ft_ultimate_range
**You must know:**  
- بحال range ولكن كتاخد `int **range`.  
- كتستعمل double pointer باش تعطي array للـ caller.  
- ترجع size ولا 0 ولا -1 إلا malloc فشلت.  

**Algorithm (concept):**  
1. إلا min >= max → `*range = NULL`, ترجع 0.  
2. Allocate `(max - min)` ints.  
3. عمر array بالقيم.  
4. رجع size.  

**Defense questions:**  
- علاش كنديرو double pointer هنا؟  
- شنو المعنى ديال return values (0, size, -1)؟  
- كيفاش تdetect allocation failure؟  

**Keywords & Concepts:**  
- double pointer  
- output parameter  
- error signaling  

---

## ex03 — ft_strjoin
**You must know:**  
- concatenate array ديال strings مع separator.  
- إلا size=0 → تخصك ترجع malloc’ed empty string.  

**Algorithm (concept):**  
1. تحسب الطول total = sum(strings) + sep*(size-1).  
2. Allocate memory.  
3. تنسخ strings وتزيد sep فالوسط.  

**Defense questions:**  
- كيفاش تحسب الطول من قبل؟  
- علاش كنرجعو malloc'ed empty string فالـ size=0؟  
- شنو risk ديال buffer overflow هنا؟  

**Keywords & Concepts:**  
- dynamic concatenation  
- buffer size calculation  
- separator logic  

---

## ex04 — ft_convert_base
**You must know:**  
- تحويل عدد من base وحدة لـ base أخرى.  
- خاصك تدير validation للبases.  
- خاصك تعرف تعامل مع negative numbers.  

**Algorithm (concept):**  
1. Validate bases: ما يكونوش مكررين، ≥ 2 chars، بلا `+` ولا `-`.  
2. Parse string → integer (بحال `atoi_base`).  
3. Convert int → base_to (recursion / loop).  
4. Return malloc’ed result.  

**Defense questions:**  
- كيفاش كاتvalidate base string؟  
- علاش recursion مزيانة هنا؟  
- شنو كيدير modulo/division algorithm فالconversion؟  
- كيفاش تتعاملو مع `INT_MIN`؟  

**Keywords & Concepts:**  
- base validation  
- atoi logic  
- recursion  
- modulo/division algorithm  

---

## ex05 — ft_split
**You must know:**  
- تقسيم string باستعمال charset كـ separators.  
- ترجع array ديال strings، NULL terminated.  
- ما خصش يكونو empty strings.  

**Algorithm (concept):**  
1. Count words (non-separator sequences).  
2. Allocate array of char\*.  
3. Allocate strings لكل word وتنسخ chars.  
4. دير NULL فالآخر.  

**Defense questions:**  
- كيفاش كتعرف boundaries ديال word؟  
- علاش كنمنعو empty strings؟  
- شنو هي complexity (O(n))؟  
- كيفاش خاصك تتعامل مع memory leaks إلا malloc فشلت؟  

**Keywords & Concepts:**  
- string tokenization  
- dynamic arrays  
- memory management  
- NULL-terminated array  

---

# 🧰 Core Algorithms Concepts (C07)

- **Linear scan + malloc copy** → (ft_strdup).  
- **Range generation** → (ft_range, ft_ultimate_range).  
- **Concatenation with pre-calculated size** → (ft_strjoin).  
- **Parsing + conversion** (atoi_base + putnbr_base) → (ft_convert_base).  
- **Tokenization & word counting** → (ft_split).  
- **Validation routines** → (malloc checks, base validation).  
