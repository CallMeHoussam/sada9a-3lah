
# 42 Piscine — Shell 01
---
## ex01 — print_groups
**خاصك تعرف:**
- environment variable `$FT_USER`.  
- كيفاش تجيب groups ديال user (`groups`, `id -Gn`).  
- كيفاش تبدل الفراغ بـ `,`.  

**Defense questions:**
- شنو الفرق بين `groups` و `id -Gn`؟  
- كيفاش shell كيوسّع `$FT_USER`؟  
- علاش استعملنا `tr ' ' ','`؟  

**Tests:**
```sh
export FT_USER=nours
./print_groups.sh
# output: god,root,admin,master,nours,bocal
````

**Keywords & Concepts:**

* **Environment variable**.
* **Command substitution**: `$(...)`.
* **id vs groups**.

---

## ex02 — find\_sh

**خاصك تعرف:**

* أمر `find` مع option `-name '*.sh'`.
* كيفاش تحيد `.sh` من الأسامي (`basename`, `cut`, `sed`).

**Defense questions:**

* الفرق بين `find . -name "*.sh"` و `ls *.sh`؟
* كيفاش تعمل recursive search؟
* شنو الفرق بين basename و cut؟

**Tests:**

```sh
touch test.sh subdir/other.sh
./find_sh.sh
# output: test, other
```

**Keywords & Concepts:**

* **find**.
* **basename**.
* **pipes**.

---

## ex03 — count\_files

**خاصك تعرف:**

* كيفاش تستعمل `find .` مع `wc -l`.
* خاص تعدّ directories و files بجوج.

**Defense questions:**

* الفرق بين `-type f` و `-type d`؟
* علاش `ls | wc -l` ماشي كافي؟
* واش `.` محسوبة كـ directory؟

**Tests:**

```sh
mkdir testdir
touch file1 file2
./count_files.sh
```

**Keywords & Concepts:**

* **find**.
* **wc -l**.
* **file types**.

---

## ex04 — MAC

**خاصك تعرف:**

* شنو هو MAC address.
* كيفاش تلقاه بـ `ifconfig` ولا `ip link`.

**Defense questions:**

* الفرق بين MAC و IP address؟
* علاش كيستعملو hexadecimal؟
* واش VM كتأثر على MAC؟

**Tests:**

```sh
ifconfig | grep ether
ip link | grep link/ether
```

**Keywords & Concepts:**

* **MAC**: Media Access Control.
* **Hexadecimal**.
* **Network interface**.

---

## ex05 — Can you create it?

**خاصك تعرف:**

* كيفاش تخلق file باسمية فيها special chars.
* escaping بالـ backslash ولا quotes.
* المحتوى فيه غير `42`.

**Defense questions:**

* كيفاش تدير file لي كيبدأ بـ `?`, `$`, `'`؟
* كيفاش تتأكد فيه غير `42\n`؟
* الفرق بين `echo` و `printf`؟

**Tests:**

```sh
ls -lRa *MaRV*
cat "\?$*'MaRViN'*$?\"
```

**Keywords & Concepts:**

* **Escaping special chars**.
* **Quoting rules**.
* **cat -e**.

---

## ex06 — Skip

**خاصك تعرف:**

* كيفاش تطبع line وتخلي line.
* أوامر: `sed`, `awk`, `nl`, `grep`.

**Defense questions:**

* كيفاش تجيب odd/even lines؟
* شنو كيدير `awk 'NR % 2'`؟
* الفرق بين sed و awk؟

**Tests:**

```sh
ls -l | ./skip.sh
```

**Keywords & Concepts:**

* **sed**.
* **awk**.
* **line addressing**.

---

## ex07 — r\_dwssap

**خاصك تعرف:**

* structure ديال `/etc/passwd`.
* مراحل:

  1. تحيد comments.
  2. تختار lines زوجية.
  3. تجيب logins.
  4. تدير reverse.
  5. sort reverse.
  6. تختار بين `$FT_LINE1` و `$FT_LINE2`.
  7. join بـ `, ` وتسالي بـ `.`.

**Defense questions:**

* شنو كيحتاوي كل field فـ `/etc/passwd`؟
* الفرق بين cut و awk؟
* علاش استعملنا `rev`؟
* الفرق بين `sort` و `sort -r`؟

**Tests:**

```sh
export FT_LINE1=7 FT_LINE2=15
./r_dwssap.sh
```

**Keywords & Concepts:**

* **cut -d ':'**.
* **awk -F ':'**.
* **rev**.
* **sort -r**.

---

## ex08 — add\_chelou

**خاصك تعرف:**

* system ديال bases خاصة (custom numeral system).
* mapping ديال symbols → digits.
* كيفاش تدير conversion مع `tr` + `bc`.

**Defense questions:**

* كيفاش تحوّل من base خاصة لـ decimal؟
* علاش استعملنا `tr`؟
* كيفاش خدمنا بـ `bc`؟
* شنو هو target base (`gtaio luSnemf`)?

**Tests:**

```sh
export FT_NBR1="\\'?\"\\\"'\\?"
export FT_NBR2="rcrdmddd"
./add_chelou.sh
```

**Keywords & Concepts:**

* **tr**.
* **bc**.
* **custom base alphabets**.

---

# 🧰 Core Concepts (Shell 01)

* **Environment variables**: export, \$VAR.
* **Quoting/Escaping**: `'...'`, `"..."`, `\`.
* **Redirections & pipes**.
* **Regex vs globbing**.
* **Text processing tools**: `cut`, `awk`, `sed`, `rev`, `tr`.
* **Base conversion** مع `bc`.
* **Special filenames**.

```

