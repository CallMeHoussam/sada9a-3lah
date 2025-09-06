
# 1337 Piscine — C 09 

هاد الموديول كيعلمك **libraries**, **Makefiles** و **string splitting مع malloc**.  
فـ defense غادي يسولوك بزاف على:  
- الفرق بين static library و dynamic library  
- compilation rules فالـ Makefile  
- parsing algorithms و memory leaks  

---

## ex00 — libft

**You must know:**
- خاصك تصايب static library سميتها `libft.a`.  
- خاصك دير functions:  
  - `ft_putchar` (تكتب char واحد بـ write)  
  - `ft_swap` (تبدل جوج ints)  
  - `ft_putstr` (تكتب string)  
  - `ft_strlen` (تحسب الطول ديال string)  
  - `ft_strcmp` (تقارن strings).  
- خاصك تستعمل script: `libft_creator.sh` باش تدير compile و archive.  
- Commands المستعملة: `gcc -c`, `ar rc`, `ranlib`.  

**Defense questions:**
- شنو هي static library؟ وشنو الفرق بينها وبين dynamic library؟  
- شنو الدور ديال `ar`, `ranlib`, `gcc -c`؟  
- علاش استعملنا write وماشي printf؟  
- علاش `.a` وماشي `.so`؟  

**Tests:**
```bash
sh libft_creator.sh
ar t libft.a          # تشوف المحتوى
gcc main.c libft.a && ./a.out

**Keywords & Concepts:**

* static library (`.a`)
* archiver (`ar rc`)
* indexing library (`ranlib`)
* compilation vs linking

---

## ex01 — Makefile

**You must know:**

* خاصك تصايب Makefile باش يدير automate للـ compilation ديال `libft.a`.
* الملفات: sources فـ `srcs/` و headers فـ `includes/`.
* rules ضروريين: `all`, `clean`, `fclean`, `re`, `libft.a`.
* ماخصوش يعاود يدير recompilation إلا تبدل شي file.

**Defense questions:**

* شنو هما rules و targets ديال Makefile؟
* الفرق بين `clean` و `fclean`؟
* علاش كنستعمل `-Wall -Wextra -Werror`؟
* كيفاش `make` كيعرف واش خاصو يعاود يدير compile ولا لا؟

**Tests:**

```bash
make        # يبني libft.a
make clean  # يحيد .o files
make fclean # يحيد .o و libft.a
make re     # clean + rebuild
```

**Keywords & Concepts:**

* Makefile rules
* dependencies
* phony targets (`.PHONY`)
* incremental compilation

---

## ex02 — ft\_split

**You must know:**

* Prototype:

  ```c
  char **ft_split(char *str, char *charset);
  ```
* خاصك تقسّم string `str` باستعمال أي char من `charset` كـ separator.
* كترجع array ديال strings (NULL-terminated).
* ماخصش يكونو empty strings.
* تستعمل malloc لكل كلمة و للـ array.

**Algorithm (concept):**

1. دير scan للـ string و count ديال الكلمات (skip separators).
2. دير malloc للـ array ديال char\* (عدد الكلمات + 1).
3. لكل كلمة:

   * حدد البداية والنهاية.
   * دير malloc و copy.
4. حط NULL فالآخر.
   → **Parsing + dynamic allocation algorithm**.

**Defense questions:**

* كيفاش كتعرف separator؟
* علاش خاص الـ array يسالي بـ NULL؟
* كيفاش تمنع memory leaks إلا malloc فشل؟
* شنو هي complexity ديال split؟ (O(n\*m) مع charset lookup).
* الفرق بين `strtok` (فالـ C library) و implementation ديالك؟

**Tests:**

```c
char **tab = ft_split("Hello,World 42 Piscine!", " ,!");
for (int i = 0; tab[i]; i++)
    printf("[%s]\n", tab[i]);
// Output: [Hello] [World] [42] [Piscine]
```

**Keywords & Concepts:**

* dynamic allocation
* parsing algorithm
* delimiter set (charset)
* NULL-terminated arrays
* memory leaks & free()

---

# 🧰 Core Algorithms & Concepts for C09

* **Static library creation** → `ar`, `ranlib`
* **Makefile automation** → dependencies, rules, clean/rebuild
* **Parsing algorithm for split** → scan, skip, extract words
* **Dynamic allocation** strategies
* **NULL-termination** convention
* **Error handling** فـ malloc failures

```
