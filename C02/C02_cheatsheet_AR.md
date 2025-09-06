# 1337 Piscine — C 02 

هاد الموديول مركز بزاف على **strings**:  
- copy (نسخ)  
- validation (تحقق واش حروف أو أرقام)  
- transformation (uppercase/lowercase/capitalize)  
- visualization (memory dump, hex)  

خاصك تكون فاهم algorithms لي مخبيين ورا كل تمرين، حيت فالـ defense غادي يسولوك على **الفكرة** ماشي غير الكود.

---

## ex00 — ft_strcpy
**You must know:**  
- كاتعاود `strcpy`.  
- تنسخ string من `src` ل `dest` حتى توصل `'\0'`.  

**Algorithm (concept):**  
- **Sequential copy** → كدوز char ب char وتنسخ حتى null terminator.  

**Defense questions:**  
- علاش ضروري تنسخ `'\0'`؟  
- شنو يوقع إلا `dest` صغير؟  

**Keywords & Concepts:**  
- string copy, null terminator, buffer overflow.

---

## ex01 — ft_strncpy
**You must know:**  
- نفس بحال strcpy ولكن مع `n`.  
- إلا `src` قصير → يكمل padding بـ `'\0'`.  

**Algorithm (concept):**  
- **Fixed-length copy** → كاتنسخ حتى `n` chars، إلا ماكملش كاتعمر بالباقي `\0`.  

**Defense questions:**  
- إلا `n` < طول `src` شنو يوقع؟  
- علاش padding مهم؟  

**Keywords & Concepts:**  
- partial copy, zero-padding, fixed buffer.

---

## ex02 — ft_str_is_alpha
**You must know:**  
- ترجّع 1 إلا كامل string فيه غير حروف.  
- Empty string → 1.  

**Algorithm (concept):**  
- **Validation scan** → تفركس كل char واش داخل range A–Z ولا a–z.  

**Defense questions:**  
- علاش empty string كتعتبر valid؟  

**Keywords & Concepts:**  
- ASCII ranges, alpha validation.

---

## ex03 — ft_str_is_numeric
**You must know:**  
- ترجّع 1 إلا كامل string digits.  

**Algorithm (concept):**  
- **Digit validation** → كل char خاصو يكون بين '0' و '9'.  

**Defense questions:**  
- شنو الكود ASCII ديال '0' و '9'؟  

**Keywords & Concepts:**  
- numeric validation, ASCII codes.

---

## ex04 — ft_str_is_lowercase
**You must know:**  
- ترجّع 1 إلا كامل string lowercase.  

**Algorithm (concept):**  
- **Range check** → كل char خاصو يكون بين 'a' و 'z'.  

**Defense questions:**  
- علاش خاصك تستعمل range وماشي شرط حرف بحرف؟  

**Keywords & Concepts:**  
- lowercase validation, ASCII range.

---

## ex05 — ft_str_is_uppercase
**You must know:**  
- نفس بحال الفوق ولكن Uppercase.  

**Algorithm (concept):**  
- **Range check** → كل char بين 'A' و 'Z'.  

**Defense questions:**  
- شنو يوقع إلا string فيه mixed case؟  

**Keywords & Concepts:**  
- uppercase validation, ASCII.

---

## ex06 — ft_str_is_printable
**You must know:**  
- printable ASCII = 32 حتى 126.  

**Algorithm (concept):**  
- **Validation** → كل char خاصو يكون فهاد range.  

**Defense questions:**  
- علاش `\n` ماشي printable؟  
- شنو هو ASCII 127؟  

**Keywords & Concepts:**  
- printable chars, control chars, ASCII table.

---

## ex07 — ft_strupcase
**You must know:**  
- تحول كل lowercase → uppercase.  

**Algorithm (concept):**  
- **Case transformation** → تستعمل offset ديال 32 فـ ASCII.  

**Defense questions:**  
- علاش الفرق بين lowercase و uppercase = 32؟  

**Keywords & Concepts:**  
- ASCII arithmetic, case conversion.

---

## ex08 — ft_strlowcase
**You must know:**  
- تحول العكس: uppercase → lowercase.  

**Algorithm (concept):**  
- **Case transformation** → تضيف 32 باش تولي small letter.  

**Defense questions:**  
- علاش كنخدمو in-place وماشي كنرجعو string جديد؟  

**Keywords & Concepts:**  
- case transformation, mutability.

---

## ex09 — ft_strcapitalize
**You must know:**  
- أول حرف ديال كل word → Uppercase.  
- الباقي → lowercase.  
- Word = حروف + أرقام.  

**Algorithm (concept):**  
- **Parsing with boundaries** → تحدد بداية word، تدي uppercase، والباقي lowercase.  

**Defense questions:**  
- شنو كيحدد boundaries ديال word؟  

**Keywords & Concepts:**  
- tokenization, parsing, capitalization.

---

## ex10 — ft_strlcpy
**You must know:**  
- نسخة safe من copy.  
- ترجع طول `src` كامل.  
- كاتحاول copy حتى `size-1` chars وكتخلي null terminate.  

**Algorithm (concept):**  
- **Safe copy with truncation detection** → بحال strncpy ولكن كيأكد ديما null terminate وكيعطيك length.  

**Defense questions:**  
- علاش مهم ترجع طول `src`؟  
- إلا size=0 شنو يوقع؟  

**Keywords & Concepts:**  
- safe string copy, truncation, buffer management.

---

## ex11 — ft_putstr_non_printable
**You must know:**  
- تطبع string.  
- إلا char ماشي printable → كتبدلو بـ `\xx` فالـ hex.  

**Algorithm (concept):**  
- **Hex encoding** → non-printable chars كيتبدلو بالـ escape sequence فالـ hex (always 2 digits).  

**Defense questions:**  
- علاش استعملو hex وماشي decimal؟  

**Keywords & Concepts:**  
- escape sequences, hex representation, formatting.

---

## ex12 — ft_print_memory
**You must know:**  
- كتوري memory بحال hex dump.  
- 3 columns: address, hex values, ASCII.  
- Non-printable → dot.  

**Algorithm (concept):**  
- **Hex dump algorithm** →  
  1. Print address (فـ hex).  
  2. Print content فـ hex مع spacing.  
  3. Print ASCII representation.  
  4. Non-printables → `.`  

**Defense questions:**  
- علاش كيتقسم memory لـ 16 bytes per line؟  
- الفرق بين pointer arithmetic و array indexing؟  

**Keywords & Concepts:**  
- memory dump, hex formatting, pointer arithmetic.

---

# 🧰 Core Algorithms Concepts في C02
- **Sequential copy** (ft_strcpy).  
- **Fixed-length copy with padding** (ft_strncpy).  
- **Validation scans** (alpha, numeric, lowercase, uppercase, printable).  
- **Case transformations** (strupcase, strlowcase).  
- **Parsing & word-boundaries** (strcapitalize).  
- **Safe copy with truncation detection** (strlcpy).  
- **Formatting & encoding** (ft_putstr_non_printable, ft_print_memory).  
