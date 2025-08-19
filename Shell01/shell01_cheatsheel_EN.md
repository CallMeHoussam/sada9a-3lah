# 📘 42 Piscine — Shell 01 (Deep Preparation Guide)

---

## ex01 — print\_groups

**You must know:**

* `$FT_USER` environment variable.
* How to list groups a user belongs to.
* How to format output with commas but no spaces.

**Defense questions:**

* What’s the difference between `groups` and `id -Gn`?
* How does the shell expand `$FT_USER`?
* Why do we need `tr ' ' ','`?

**Tests:**

```sh
export FT_USER=nours
./print_groups.sh
# should print: god,root,admin,master,nours,bocal
```

**Keywords & Concepts:**

* **Environment variable**: `$FT_USER`.
* **Command substitution**: `$(...)`.
* **id vs groups**: both show group membership.

---

## ex02 — find\_sh

**You must know:**

* `find` command basics.
* Pattern matching with `-name '*.sh'`.
* Removing `.sh` extension (`basename`, `sed`, `cut`).

**Defense questions:**

* What’s the difference between `find . -name "*.sh"` and `ls *.sh`?
* Why use `basename` or parameter expansion?
* How to ensure recursive search?

**Tests:**

```sh
touch test.sh subdir/other.sh
./find_sh.sh
# expected: test, other
```

**Keywords & Concepts:**

* **find**.
* **Basename**.
* **Pipes & redirections**.

---

## ex03 — count\_files

**You must know:**

* `find` + `wc -l`.
* Count **both files and directories**, including `.`.

**Defense questions:**

* Difference between regular files (`-type f`) and directories (`-type d`)?
* How to include `.` in count?
* Why is `ls | wc -l` not enough?

**Tests:**

```sh
mkdir testdir
touch file1 file2
./count_files.sh   # should count files + dirs
```

**Keywords & Concepts:**

* **wc -l**: counts lines.
* **find .** includes `.`.
* **Regular file vs directory**.

---

## ex04 — MAC

**You must know:**

* MAC addresses (unique hardware address).
* How to use `ifconfig` or `ip link`.

**Defense questions:**

* Difference between IP and MAC address?
* Why do MAC addresses use hex?
* How do virtual machines affect MACs?

**Tests:**

```sh
ifconfig | grep ether
ip link | grep link/ether
```

**Keywords & Concepts:**

* **MAC**: Media Access Control.
* **Hexadecimal** format.
* **Network interfaces**.

---

## ex05 — Can you create it?

**You must know:**

* How to create a file with a special name containing special characters.
* Escaping in shell: backslashes and quotes.
* File must contain only `42`.

**Defense questions:**

* How to create files with names starting with `?`, `$`, or quotes?
* How to check file really has only `42` and newline?
* What’s the difference between `echo "42"` and `printf "42\n"`?

**Tests:**

```sh
ls -lRa *MaRV*
cat "\?$*'MaRViN'*$?\"
```

**Keywords & Concepts:**

* **Escaping special chars**.
* **Quoting rules**: single vs double quotes.
* **cat -e** to check newline.

---

## ex06 — Skip

**You must know:**

* How to print one line out of two.
* Tools: `awk`, `sed -n`, `nl`, `grep` with regex.

**Defense questions:**

* How to select only odd/even lines?
* What does `sed -n 'p'` mean?
* Why do we start from the first line?

**Tests:**

```sh
ls -l | ./skip.sh
```

**Keywords & Concepts:**

* **sed**.
* **awk NR%2**.
* **Line addressing**.

---

## ex07 — r\_dwssap

**You must know:**

* `/etc/passwd` format.
* How to:

  1. Remove comments.
  2. Keep every other line (starting from 2nd).
  3. Extract logins.
  4. Reverse them.
  5. Sort in reverse order.
  6. Select between `$FT_LINE1` and `$FT_LINE2`.
  7. Join with `, ` and end with `.`.

**Defense questions:**

* What does each field in `/etc/passwd` mean?
* How to extract only login names?
* Difference between `cut -d:` and `awk -F:`?
* Why reverse the string with `rev`?

**Tests:**

```sh
export FT_LINE1=7 FT_LINE2=15
./r_dwssap.sh
```

**Keywords & Concepts:**

* **cut/awk**.
* **rev**.
* **sort -r**.
* **head/tail**.

---

## ex08 — add\_chelou

**You must know:**

* Custom numeral systems.
* Mapping symbols to digits.
* Base conversion with `tr` + `bc`.

**Defense questions:**

* How do you convert from a custom base to decimal?
* Why do we use `tr`?
* How do we pipe into `bc`?
* What’s the target base (`gtaio luSnemf`)?

**Tests:**

```sh
export FT_NBR1="\\'?\"\\\"'\\?"
export FT_NBR2="rcrdmddd"
./add_chelou.sh
```

**Keywords & Concepts:**

* **tr** (translate characters).
* **bc** (arbitrary precision calculator).
* **Custom alphabets for base systems**.

---

# 🧰 Core Concepts for Shell 01

* **Environment variables** (`export`, `$VAR`).
* **Quoting and escaping** (single, double, backslash).
* **Redirections and pipes**.
* **Regex vs globbing** (`find`, `grep`).
* **Standard input/output**.
* **Text processing**: `cut`, `awk`, `sed`, `rev`, `tr`.
* **Number bases**: converting with `bc`.
* **File naming**: handling special characters.
