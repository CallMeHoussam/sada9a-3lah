# 42 Piscine — C01 README ديال التحضير (Darija + Technical Terms)

هاد الڤايد فيه كلشي باش توجد لموديول C01 فالـ 42، وغادي تلقى:
- **خاصك تعرف:** المفاهيم الأساسية لي لازم تفهمها.
- **Defense questions:** الأسئلة لي ممكن يسولك عليهم فـ evaluation.
- **Tests:** كيفاش تختبر الكود والحالات القصوى.
- **Keywords & Concepts:** مصطلحات تقنية بالإنجليزية لازم تحفظهم.

---

## 📜 General Rules
- سيفط غير الملفات لي طالبينك وبنفس الأسماء والمجلدات.
- أغلب التمارين مفيهمش دوال مسموحة، غير `write` فـ `ft_putstr`.
- الكمبايل بـ: `gcc -Wall -Wextra -Werror` (أي warning = error).
- الخرج خاصو يكون مطابق حرفياً، استعمل `./a.out | cat -e` باش تشوف المسافات والـ newline.
- دوز `norminette -R CheckForbiddenSourceHeader`.
- ممنوع تضيف ملفات زايدة ولا `main()` إلا إذا قالوها فالـ subject.

---

## ex00 — ft_ft
**خاصك تعرف:**
- كيفاش تبعت pointer لفنكسيون.
- كيفاش تستعمل `*` (dereference) باش تغيّر القيمة فالعنوان.

**Defense questions:**
- شنو هو pointer؟
- الفرق بين `*nbr = 42;` و `nbr = 42;`؟
- آش كيوقع إلا بعثتي NULL pointer؟

**Tests:**
- جرب تغيّر int لقيمة 42.

**Keywords & Concepts:**
- Pointer
- Dereferencing
- Indirection Operator (`*`)
- NULL pointer

---

## ex01 — ft_ultimate_ft
**خاصك تعرف:**
- Multiple Indirection (pointer داخل pointer حتى 9 مستويات).
- كيفاش توصل للأصل باش تغيّر القيمة.

**Defense questions:**
- شنو هو `int *********nbr`؟
- الفرق بين stack و heap فالذاكرة.
- واش كاين سبب عملي لهاد العمق ديال pointers؟

**Tests:**
- ربط 9 pointers مع واحد int وجرب.

**Keywords & Concepts:**
- Multiple Indirection
- Dereferencing Levels
- Memory Address Chaining

---

## ex02 — ft_swap
**خاصك تعرف:**
- Swapping values باستعمال temp variable.
- Passing by reference.

**Defense questions:**
- الفرق بين تبديل القيم وتبديل العناوين.
- علاش temp variable ضروري.

**Tests:**
- swap مع أعداد موجبة، سالبة، نفس الرقم.

**Keywords & Concepts:**
- Swap Algorithm
- Temporary Storage
- Passing by Reference

---

## ex03 — ft_div_mod
**خاصك تعرف:**
- Integer division و modulo.
- تخزين النتيجة والباقي فـ pointers.
- السلوك مع أعداد سالبة.

**Defense questions:**
- كيفاش `/` و `%` كيتعاملو مع السوالب فـ C؟
- آش كيوقع إلا b = 0؟ (Undefined Behavior)

**Tests:**
- combinations موجبة/سالبة، divisor = 1 أو -1.

**Keywords & Concepts:**
- Division Operator `/`
- Modulo Operator `%`
- Undefined Behavior (divide by zero)

---

## ex04 — ft_ultimate_div_mod
**خاصك تعرف:**
- نفس ex03 ولكن In-Place Modification.
- quotient فـ *a، remainder فـ *b.

**Defense questions:**
- الفرق بين ترجيع عبر pointer أو تعديل مباشر.
- خطر overwriting قبل ما تسالي الحساب.

**Tests:**
- نفس الحالات ديال ex03.

**Keywords & Concepts:**
- In-Place Modification
- Data Overwrite Risk
- Order of Operations

---

## ex05 — ft_putstr
**خاصك تعرف:**
- طباعة string بـ `write`.
- loop حتى توصل لـ null-terminator (`\0`).

**Defense questions:**
- الفرق بين char array و char pointer.
- شنو هو `\0` وعلاش ضروري؟
- واش `write` كيعرف فين يسالي وحدو؟

**Tests:**
- string فارغ، نص عادي، رموز خاصة.

**Keywords & Concepts:**
- Null-Terminator (`\0`)
- String Representation in C
- Standard Output

---

## ex06 — ft_strlen
**خاصك تعرف:**
- تحسب طول string حتى توصل لـ `\0`.
- ما تستعملش `<string.h>`.

**Defense questions:**
- علاش `\0` مهم فـ strings؟
- Time Complexity ديال strlen.

**Tests:**
- string فارغ، طويل، فيه مسافات.

**Keywords & Concepts:**
- String Traversal
- Time Complexity O(n)

---

## ex07 — ft_rev_int_tab
**خاصك تعرف:**
- Array reversal in-place.
- Symmetric swapping (الأول مع الآخر).

**Defense questions:**
- Indexing و pointer arithmetic.
- شحال من swap كتحتاج؟ (`size/2`).

**Tests:**
- array زوجية/فردية الطول، size=1.

**Keywords & Concepts:**
- In-Place Array Reversal
- Symmetric Swap
- Index Calculation

---

## ex08 — ft_sort_int_tab
**خاصك تعرف:**
- Sorting array ascending (Bubble Sort كافي هنا).
- Swapping حتى يترتب.

**Defense questions:**
- Time Complexity ديال algo.
- كيفاش تعرف راه array مرتبة.

**Tests:**
- array مرتبة، معكوسة، فيها duplicates، أو كلها نفس القيمة.

**Keywords & Concepts:**
- Bubble Sort
- Time Complexity O(n²)
- Stable vs Unstable Sort

---

## 💡 Extra Tips
- جرّب الحالات القصوى (NULL pointers، strings فارغة، arrays size=0 أو 1).
- Integer division فـ C كتقرّب للصفر.
- `write` ما كيضفش `\0` ولا newline — انت خاصك تتحكم فالformat.
- فتمارين pointers، حضّر تشرح Memory Diagram فالـ defense.
