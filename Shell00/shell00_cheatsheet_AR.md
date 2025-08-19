

# 🔑 Keywords & Concepts — Deep Dive (Shell 00)

## ex00 — **Z**&#x20;

* **POSIX text file**, **ASCII**: الحرف `Z` هو 0x5A، و **newline** هو 0x0A.
* **cat vs echo vs printf**: `cat` كيقرا المحتوى بلا ما يبدّل؛ `echo` يقدر يزيد newline ولا يبدّل escapes؛ `printf` أدقّ.
* **End-of-file (EOF) vs end-of-line (EOL)**: EOF ماشي كاراكتر.
* **Self-check**: `hexdump -C z` / `xxd -g1` باش تتأكد من الـ newline؛ `wc -c z` تشوف الحجم.
* **Permissions basics**: خليه readable للجميع باش `cat z` يخدم بلا sudo.

---

## ex01 — **testShell00**&#x20;

* **`ls -l` fields**: نوع الملف (file/dir/link)، **permissions** (rwx)، **hard link count (nlink)**، **owner/group**، **size**، **mtime** (ساعة ولا عام حسب النظام).
* **`chmod` octal vs symbolic**: `-r--r-xr-x` = `0455`؟ (owner=4, group=5, other=5). تعلّم التحويل بين rwx ↔ أرقام.
* **`umask`**: غادي يأثّر على الإعدادات الافتراضية.
* **`touch -t`** لضبط **timestamps** باش الشكل يقرّب للـ subject (لو بغيت).
* **`tar -cf testShell00.tar testShell00`**: **archive** بلا **compression**؛ الفرق بين **tar** و **tar.gz**.
* **`stat`** لقراءة metadata بدقّة.
* **Collation/locale**: بعض الأنظمة تبدّل عرض الوقت؛ ما تقلقش، الـ subject قابل **year بدل time**.&#x20;

---

## ex02 — **Oh yeah, mooore…**&#x20;

* **Directory vs regular file permissions**:

  * فالـ dir: `r`= list، `x`= traverse، `w`= create/delete.
* **Hard link vs symlink**:

  * **Hard link** كيشارك نفس **inode** ونفس **nlink** كيزيد؛ ما تقدّش تدير hard link لِـ dir.
  * **Symlink** هو **path reference** (يقدر يكون **dangling**).
* **Create exact sizes**: استعمل `printf` بلا newline (مثلاً `printf 'A' > test3`) باش تخرّج 1 byte؛ حذارِي من `echo` لأنه كيزيد newline.
* **Set link count=2**: `ln test3 test5` باش يكونو بجوج نفس inode ونفس size (وكيبان `2` فـ nlink).
* **Executable bit**: `chmod 714 test1` يعطي `-rwx--xr--`.
* **`ls -l` reading**: فهاذ السطر كنقرا permissions، nlink، size، التاريخ… وكنقارن مع المطلوب فـ subject.

---

## ex03 — **SSH me! (id\_rsa\_pub)**&#x20;

* **Public key vs Private key**:

  * public: كيتشارك؛ private: سرّي (`~/.ssh/id_rsa`) permissions 600.
* **`ssh-keygen`**: تولّد **RSA** (ولا **ed25519** فالعصر الحديث)؛ الsubject باغي الملف يتسمّى **`id_rsa_pub`** فـ repo (الاسم مقصود).
* **Key formats**: `ssh-rsa AAAA... user@host`؛ **fingerprint**.
* **`authorized_keys`** vs **`known_hosts`**: الأول باش تسمح بالولوج للسيرفر؛ الثاني كيحفظ بصمات السيرفر.
* **`ssh-agent` / `ssh-add`**: تدبير المفاتيح فالسيشن.

---

## ex04 — **midLS**&#x20;

* **Sorting by mtime**: `-t` (آخر تعديل)؛ direction الافتراضي: من الجديد للقديم.
* **Show directories with slash**: `-p`.
* **Comma-separated list**: `-m` كيعطي output مفصول بـ `, ` فسطّر واحد.
* **Exclude hidden**: افتراضياً `ls` ماكايبينش dotfiles؛ الـ subject كيأكد استثناء لي كيبدى بـ `.` (حتى `..`).
* **Locale stability**: تقدر تدير `LC_ALL=C` قدّام الأمر باش تضمن نفس sorting/format عبر الماكينات.
* **Filename safety**: `ls` يطبع الأسامي كما هي (حتى لو فيها spaces).

> Hint للأمر لي كيغطي المطلوب: `LC_ALL=C ls -1mtp` ثم تنسيق، ولكن بما أن الsubject باغي “command line” بسيطة، غالباً `ls -mtp` كافية (غير ما تزيدش hidden). راجع مثال الـ subject باش تتأكد من الformat لي باغيه.

---

## ex05 — **GiT commit**&#x20;

* **Commit IDs**: **SHA-1** full hash.
* **`git log -n 5 --format=%H`** باش تجيب آخر 5.
* **Porcelain vs plumbing**: `git rev-parse HEAD`، ranges بحال `HEAD~4..HEAD`.
* **Script portability**: خليه يطبع newline واحد لكل سطر (باش `| cat -e` يبين `$`).
* **No env assumptions**: المولينيط كيشغّل سكريبتك فبيئة ديالهم.

---

## ex06 — **gitignore**&#x20;

* **Ignore patterns (glob)**: `*`, `?`, `**`, النهاية بـ `/` كتعني dir فقط.
* **Negation**: `!pattern` كيلغي ignore سابق.
* **Hierarchy**: `.gitignore` فـ project، و **global excludes** (بحال `.DS_Store`).
* **Listing ignored files فعلاً موجودة**:

  * آمن: `git ls-files --others -i --exclude-standard` (untracked & ignored).
  * Debug: `git check-ignore -v <path>`.
* **Caveat**: `gitignore` ماكيحيدش ملفات **already tracked**.

---

## ex07 — **diff**&#x20;

* **`diff` formats**: unified (`-u`), context (`-c`), normal (default).
* **Whitespace/newline sensitivity**: `cat -e` كيبيّن `$` فآخر السطر؛ انتبه لـ LF vs CRLF.
* **`patch`**: `patch < sw.diff`، و `-pN` باش تقصّ المسارات.
* **Exit status**: 0 = no diff، 1 = differences موجودة، >1 = error.
* **`diff -w`** كيتجاهل spaces (ما تستعملوش إلا إذا طلبوه).

---

## ex08 — **clean**&#x20;

* **`find` predicates**: `-type f`, `-name`, grouping `\( … -o … \)`.
* **Print & delete فـ “command واحد”**:

  * GNU/BSD: `find . -type f \( -name '*~' -o -name '#*#' \) -print -delete`
  * Portable: `find . -type f \( -name '*~' -o -name '#*#' \) -print -exec rm -f {} +`
* **Prune `.git`** (اختياري باش ما تمسح حتى شي حاجة داخل repo metadata):

  * `find . -name .git -prune -o \( -type f \( -name '*~' -o -name '#*#' \) -print -delete \)`
* **Globbing vs regex**: `find -name` كيستعمل **glob** ماشي **regex** (إلا استعملت `-regex`).

---

## ex09 — **Illusions, not tricks, Michael… (ft\_magic)**&#x20;

* **`file(1)` magic database**: **magic rules** كتحدد signature فـ offset ونوع **type test** (string, byte, short, long…).
* **Offset counting**: magic كيخدم بـ **0-based offset**؛ “الـ 42nd byte” فالكلام البشري = offset 41. تحقّق بـ `xxd` قبل.
* **Magic line example** (فهم فقط):

  * `41  string  42    42 file`
  * كتقول: فـ offset 41 لقينا string "42" ⇒ عطي اسم النوع "42 file".
* **Testing magic**: `file -m ft_magic <file>`؛ جمع فعلاً **42** فداك البايت بـ `dd` ولا `printf` مع padding.
* **Continuations**: تقدر تزيد سطور `>` باش تشترط شروط إضافية (مش مطلوب هنا، ولكن مفيد للديفونس).

---

# 🧰 Core Shell Concepts (للديفونس والأسئلة “المفاجِئة”)

* **/bin/sh vs bash**: تجنّب **bashisms** (مثلاً `[[ ... ]]`, brace expansion المتقدّم)؛ stick لـ POSIX sh.&#x20;
* **Redirections & Pipelines**: `>`, `>>`, `<`, `2>`, `2>&1`, `|`; ترتيبهم كايْهِم.
* **Quoting**: single `'...'` (no expansion), double `"..."` (expansion ديال `$var`, backslash)، backslash escaping.
* **Command substitution**: `` `...` `` و `$(...)` (فضّل الثانية).
* **Exit status**: `$?`؛ 0 نجاح، غير 0=failure.
* **Globbing vs Regex**: shell glob (`* ? []`) ≠ `grep -E` / `sed -E` regex.
* **Filesystem**: absolute vs relative paths، `.` و `..`، **inode**، **permissions** symbolic vs octal، **suid/sgid/sticky** (كفكرة عامة).
* **Time stamps**: **atime/mtime/ctime**؛ `touch` يبدّل mtime/atime، و `chmod` يقدر يبدّل ctime.
* **Locale/encoding**: `LC_ALL=C` لتوحيد sorting/format؛ **UTF-8** vs ASCII.
* **Safety**: تعامل مع filenames فيها spaces/newlines، استعمل quotes `"*"` و `{}` فـ `find -exec`.

