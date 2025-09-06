# 1337 Piscine — C 08 (بالدارجة المغربية)

هاد الموديول ديال C08 كيعلمك:  
- **headers** (ملفات `.h`)  
- **macros** (ديال #define)  
- **structs** (باش تجمع data)  
- **dynamic allocation مع structs**  
- **كيفاش تعرض data structured فالـ output**  

فـ defense غادي يسولك بزاف على:  
- الفرق بين header و source file  
- علاش خاصنا macros و فين نستعملو functions  
- memory layout ديال struct  
- dynamic allocation و deep copy  

---

## ex00 — ft.h
**You must know:**  
- دير header file فيه prototypes ديال:  
  - ft_putchar  
  - ft_swap  
  - ft_putstr  
  - ft_strlen  
  - ft_strcmp  
- تستعمل include guards (#ifndef / #define / #endif).  

**Defense questions:**  
- علاش خاصنا prototypes فالـ header؟  
- الفرق بين `.h` و `.c`؟  
- شنو يوقع إلا نفس header تincluded مرات بزاف؟  

**Keywords & Concepts:**  
- header file  
- function prototypes  
- include guards  

---

## ex01 — ft_boolean.h
**You must know:**  
- تعرف macros باش تدير boolean system.  
- خاصك تعرف:  
  - TRUE, FALSE  
  - EVEN(nbr)  
  - EVEN_MSG, ODD_MSG  
  - SUCCESS  

**Defense questions:**  
- علاش استعملنا macros وما استعملناش enum؟  
- كيفاش كيتوسع macro EVEN(nbr)؟  
- علاش `(nbr % 2 == 0)` وماشي `(nbr & 1)`؟  

**Keywords & Concepts:**  
- macros (#define)  
- conditional macros  
- boolean simulation  

---

## ex02 — ft_abs.h
**You must know:**  
- تدير macro ABS(Value) كترجع absolute value.  
- تستعمل ternary operator.  

**Defense questions:**  
- علاش كنستعملو parentheses فـ macro؟  
- الفرق بين macro و inline function؟  
- شنو المشكل إلا درنا ABS(x++)؟  

**Keywords & Concepts:**  
- macro expansion  
- ternary operator  
- side effects  

---

## ex03 — ft_point.h
**You must know:**  
- تعرف struct s_point فيها:  
  - int x;  
  - int y;  
- تستعمل typedef باش تولي t_point.  

**Defense questions:**  
- الفرق بين struct و typedef struct؟  
- كيفاش كيتخزن struct فالذاكرة؟  
- كيفاش توصل لmembers مع pointer؟ (point->x).  

**Keywords & Concepts:**  
- structs  
- dot vs arrow operator  
- memory layout  

---

## ex04 — ft_strs_to_tab
**You must know:**  
- تبني array ديال structs من array ديال strings.  
- struct خاصو يكون فيه:  
  - int size;  
  - char *str; (original)  
  - char *copy; (malloc copy).  
- آخر عنصر خاص str = 0 (sentinel).  

**Defense questions:**  
- علاش ضروري deep copy؟  
- الفرق بين shallow copy و deep copy؟  
- كيفاش تتعامل إلا malloc فشلت؟  
- علاش كنستعمل sentinel str = 0؟  

**Keywords & Concepts:**  
- malloc/free  
- deep vs shallow copy  
- sentinel value  

---

## ex05 — ft_show_tab
**You must know:**  
- تعرض الـ struct array لي درتي فـ ex04.  
- خاصك تطبع:  
  - str  
  - size  
  - copy  
- غير بـ write (ماشي printf).  

**Defense questions:**  
- علاش استعملنا write وماشي printf؟  
- كيفاش نحولو int لـ string باش نطبعوه؟ (recursion).  
- شنو يوقع إلا copy تبدلات؟  

**Keywords & Concepts:**  
- struct traversal  
- recursion فالطبع ديال int  
- low-level output  

---

# 🧰 Core Algorithms & Concepts (C08)

- include guards باش تمنع multiple inclusion.  
- الفرق بين macros و inline functions.  
- ternary operator.  
- struct definition و memory layout.  
- استعمال pointer access (->).  
- dynamic allocation ديال struct arrays.  
- الفرق بين deep copy و shallow copy.  
- sentinel values (بحال str = 0 بحال null-terminated).  
- write() كـ low-level I/O.  
