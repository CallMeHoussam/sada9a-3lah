# 42 Piscine — C 09 (بالدارجة المغربية)

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
