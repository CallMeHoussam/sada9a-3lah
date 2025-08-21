# 1337 Piscine — C 06 

هاد الـmodule كيعلمك كيفاش تخدم مع **command-line arguments (`argc`, `argv`)** و كيفاش تستعمل loops و algorithms بحال **reverse** و **sorting**.  
فالديفونس غادي يسولوك بزاف على **ASCII order, pointer arithmetic, algorithm complexity**.  

---

## ex00 — ft_print_program_name
**خاصك تعرف:**
- خاص البرنامج يطبع الاسم ديالو (`argv[0]`).  
- مسموح غير بـ `write`.  

**Algorithm:**  
- دير loop على الحروف ديال `argv[0]`.  
- طبعهم واحد بواحد بـ `write`.  

**Defense questions:**
- `argv[0]` فيه ديما شنو؟  
- واش البرنامج كيكون ديما `./a.out`؟ (لا، كيختلف حسب شنو كتبتي فـterminal).  
- الفرق بين `argc` و `argv`؟  

**Keywords & Concepts:**
- **argc** = argument count.  
- **argv** = argument vector (array of strings).  
- **argv[0]** = program name.  

---

## ex01 — ft_print_params
**خاصك تعرف:**
- خاصك تطبع جميع الـarguments لي تعطات فالبرنامج، كل واحد فـline بوحدو.  
- كاتسالا `argv[0]`.  

**Algorithm:**  
- Loop من i=1 حتى argc-1.  
- طبع `argv[i]` character by character.  

**Defense questions:**
- علاش مانطبعوش `argv[0]`؟  
- كفاش كيتفرقو الـarguments فالـterminal؟  
- شنو كيوقع إلا مكاينش arguments؟  

**Keywords & Concepts:**
- **argv array of strings**.  
- **loop on argc**.  
- **I/O بـwrite**.  

---

## ex02 — ft_rev_params
**خاصك تعرف:**
- تطبع الـarguments بالـreverse order.  

**Algorithm:**  
- Loop من argc-1 حتى 1.  
- طبع كل argument.  

**Defense questions:**
- الفرق بين reverse ديال characters و reverse ديال arguments؟  
- واش reverse ديما O(n)؟  
- واش كاين مشكل إلا مكاينش arguments؟  

**Keywords & Concepts:**
- **reverse iteration**.  
- **array indexing**.  
- **order in memory**.  

---

## ex03 — ft_sort_params
**خاصك تعرف:**
- خاصك sort arguments حسب **ASCII order**.  
- وتطبع كل واحد فـline بوحدو.  

**Algorithm (Bubble Sort):**  
```

for i from 1 to argc-1:
for j from i+1 to argc-1:
if strcmp(argv\[i], argv\[j]) > 0:
swap(argv\[i], argv\[j])

```

**Defense questions:**
- علاش sorting حسب ASCII وماشي dictionary order؟  
- كفاش خدامة `strcmp` من الداخل؟  
- شحال complexity ديال bubble sort؟  
- واش ممكن تستعمل sorting algorithm آخر بحال quicksort؟  

**Keywords & Concepts:**
- **sorting algorithms** (Bubble Sort, Selection Sort).  
- **ASCII lexicographic order**.  
- **string comparison (strcmp)**.  
- **pointer swapping**.  

---

# 🧰 Algorithms مهمين فـ C06
- **linear scan** → لطبع program name و arguments.  
- **loop iteration** → باش تطبع argv elements.  
- **reverse iteration** → باش تطبع arguments بالعكس.  
- **sorting algorithms** → bubble sort / selection sort (O(n²)).  
- **string comparison بالASCII values**.  

---

# ⚡ Defense Traps فـ C06
- الفرق بين `argv[0]` و arguments الحقيقيين.  
- ASCII order vs alphabetical order (capital letters كيجيّو قبل small letters).  
- Complexity ديال sorting algorithms.  
- واش ممكن argument يكون empty string؟ (إيه).  
- شنو كيوقع إلا argument طويل بزاف؟ (مكاينش مشكل، غير string أطول).  
- علاش خاصنا نستعمل غير `write`؟ (باش نتعلمو low-level string handling).  