# 1337 Piscine — C 03 

هاد الـmodule كيعلمك تعاود تكتب **string comparison, concatenation, substring functions**.  
فالديفونس كيقدرو يسولوك على **edge cases, memory handling, ASCII logic, و pointer arithmetic**.  

كل تمرين فيه:  
- **خاصك تعرف**  
- **Algorithm**  
- **Defense questions**  
- **Keywords & Concepts**  

---

## ex00 — ft_strcmp
**خاصك تعرف:**
- تعاود دير `strcmp(s1, s2)`.  
- كيقارن strings بالترتيب ديال ASCII (lexicographic order).  

**Algorithm (Lexicographic comparison):**
1. Loop على بجوج strings.  
2. إلا char مختلف → رجع الفرق `(s1[i] - s2[i])`.  
3. إلا واحد وقف → القصير هو الأصغر.  
4. إلا بجوج سالاو مع `'\0'` → رجع 0.  
→ **linear scan O(n)**.  

**Defense questions:**
- شنو هو lexicographic order؟  
- علاش كترجع الفرق ديال ASCII وماشي غير -1/0/1؟  
- إلا string واحد أقصر؟  

**Keywords & Concepts:**
- **ASCII order**.  
- **signed vs unsigned char**.  
- **null-termination**.  

---

## ex01 — ft_strncmp
**خاصك تعرف:**
- بحال `strcmp` ولكن كيقارن غير حتى `n` chars.  

**Algorithm (Prefix comparison):**
1. Loop حتى `i < n` وباقي chars ماشي `'\0'`.  
2. إلا char مختلف → رجع الفرق.  
3. إلا وصلنا لـ n أو string سالا → رجع 0.  
→ **linear prefix scan O(n)**.  

**Defense questions:**
- فاش كيوقف بكري؟  
- علاش n كيكون unsigned؟  
- شنو كيوقع إلا n=0؟  

**Keywords & Concepts:**
- **prefix comparison**.  
- **boundary cases** (n=0).  

---

## ex02 — ft_strcat
**خاصك تعرف:**
- كتزيد `src` فـآخر `dest`.  

**Algorithm (Concatenation):**
1. قلب على `'\0'` فـdest.  
2. نسخ chars ديال src.  
3. حط `'\0'` فـالآخر.  
→ **linear scan + copy O(m+n)**.  

**Defense questions:**
- الفرق بين copy و append؟  
- علاش buffer size مهم بزاف؟  

**Keywords & Concepts:**
- **concatenation**.  
- **buffer overflow risk**.  
- **pointer traversal**.  

---

## ex03 — ft_strncat
**خاصك تعرف:**
- بحال `strcat` ولكن كيزيد غير حتى nb chars.  

**Algorithm (Partial concatenation):**
1. قلب على آخر ديال dest.  
2. نسخ nb chars من src (ولا أقل إلا src قصير).  
3. ديما null-terminate.  
→ **bounded copy O(n+nb)**.  

**Defense questions:**
- علاش null-termination مضمون هنا؟  
- الفرق بين `strncat` و `strncpy`؟  

**Keywords & Concepts:**
- **partial concatenation**.  
- **null-termination rules**.  

---

## ex04 — ft_strstr
**خاصك تعرف:**
- كيقلب على أول occurrence ديال substring `to_find` فـ `str`.  

**Algorithm (Naive substring search):**
1. Loop على str.  
2. فجملة كل position، جرب match مع to_find.  
3. إلا كلو match → رجع pointer.  
4. إلا ماكانش → رجع NULL.  
→ **O(n*m) naive search**.  

**Defense questions:**
- كيفاش كتعرف إلا to_find خاوي؟  
- علاش complexity O(n*m)؟  
- الفرق بين `strstr` و `strchr`؟  

**Keywords & Concepts:**
- **substring search**.  
- **return pointer**.  
- **empty needle case**.  

---

## ex05 — ft_strlcat
**خاصك تعرف:**
- safer concatenation بحال `strlcpy` ولكن كيزيد `src`.  
- كيرجع length ديال `dest + src` (string لي كان باغي يدير).  

**Algorithm (Safe concatenation with size limit):**
1. حسب length ديال dest حتى size.  
2. إلا size ≤ dest_len → رجع size + src_len (truncation).  
3. إلا لا → نسخ chars من src حتى يبان space كافي (`size - dest_len - 1`).  
4. null-terminate.  
→ **bounded concatenation O(n+m)**.  

**Defense questions:**
- الفرق بين `strcat`, `strncat`, و `strlcat`؟  
- شنو كيعني return value ديال `strlcat`؟  
- فاش كيكون truncation؟  

**Keywords & Concepts:**
- **buffer size awareness**.  
- **truncation detection**.  
- **safe string handling**.  

---

# 🧰 Core Algorithms خاصين بـ C03
- **lexicographic comparison** → `strcmp`.  
- **prefix comparison** → `strncmp`.  
- **concatenation algorithm** → `strcat`.  
- **partial concatenation** → `strncat`.  
- **substring search O(n*m)** → `strstr`.  
- **safe concatenation with buffer size** → `strlcat`.  

# ⚡ Defense traps
- الخلط بين return values (`strcat` كيـرجع pointer، `strlcat` كيـرجع length).  
- نسيان null-termination فـ`strncat`/`strlcat`.  
- buffer overflow إلا dest صغير بزاف.  
- نساو empty string cases.  
- ما كيعرفوش complexity ديال `strstr`.  
