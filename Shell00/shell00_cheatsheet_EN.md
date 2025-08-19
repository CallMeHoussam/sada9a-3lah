# 📘 42 Piscine — Shell 00 (Deep Preparation Guide)

---

## 🌍 General Rules

* Always respect **file names and paths exactly** (case-sensitive).
* Allowed commands: standard **POSIX shell commands** (sh, not bashisms).
* Compile/test on a clean environment; evaluator may use unexpected shell versions.
* Never add extra files/directories.
* Use `cat -e` or `hexdump -C` to check invisible characters.
* Exit status matters: 0 = success, non-zero = failure.

---

## ex00 — Z

**You must know:**

* How to create a simple text file containing exactly `Z` followed by a newline.
* Difference between file content vs file name.

**Defense questions:**

* What’s the difference between `echo Z` and `printf "Z\n"`?
* Why does `echo` sometimes add extra spaces or interpret escapes?
* How can you check the file actually contains only 2 bytes (0x5A 0x0A)?

**Tests:**

```sh
cat -e z      # should show "Z$"
hexdump -C z  # should show 5a 0a
wc -c z       # should show 2
```

**Keywords & Concepts:**

* **EOF vs EOL**: EOF is not a character, EOL = newline (`\n`).
* **ASCII**: `Z` = 0x5A.
* **Permissions**: must be readable.
* **touch vs > file**: both create empty files, but `touch` updates timestamps.

---

## ex01 — testShell00

**You must know:**

* File metadata (permissions, nlink, owner, group, size, timestamps).
* How `ls -l` output is structured.
* How to package a file into a tar archive.

**Defense questions:**

* What’s the difference between a tar and a zip?
* What does the number after permissions mean (`nlink`)?
* What does `-r--r-xr-x` correspond to in octal?
* Why might `ls -l` show a year instead of time?

**Tests:**

```sh
ls -l testShell00
tar -cf testShell00.tar testShell00
shasum testShell00.tar
```

**Keywords & Concepts:**

* **tar**: archive tool, no compression unless used with gzip/bzip2.
* **umask**: default permissions mask.
* **stat**: displays metadata exactly.
* **nlink**: number of hard links to the inode.
* **Octal vs symbolic permissions**.

---

## ex02 — Oh yeah, mooore…

**You must know:**

* Directory permissions vs file permissions.
* How to create files with exact sizes.
* How to create hard links vs symbolic links.
* What “executable” means for a file.

**Defense questions:**

* Why can’t you hard-link a directory?
* What happens if the target of a symlink is deleted?
* What is the difference between `chmod 714` and `chmod u=rwx,g=--x,o=r--`?

**Tests:**

```sh
ls -li   # shows inodes and link counts
ln file1 file2   # creates a hard link
ln -s file1 symlink
chmod 714 test1
```

**Keywords & Concepts:**

* **Inode**: structure that stores metadata.
* **Hard link**: multiple names for same inode.
* **Symlink**: path reference, can dangle.
* **File size vs content**: check with `hexdump -C`.

---

## ex03 — Connect me!

**You must know:**

* Basics of SSH.
* Public/private key pairs.
* File naming conventions for SSH.

**Defense questions:**

* What is the difference between public and private key?
* Why must private key permissions be 600?
* What is `authorized_keys` vs `known_hosts`?

**Tests:**

```sh
ssh-keygen -t rsa -b 4096
ssh user@hostname -p 4242
```

**Keywords & Concepts:**

* **RSA/ed25519**: algorithms for keys.
* **ssh-agent / ssh-add**: session key manager.
* **Port number**: default 22, here 4242.

---

## ex04 — midLS

**You must know:**

* `ls` options for sorting and formatting.
* How to exclude hidden files.
* How to ensure portability across locales.

**Defense questions:**

* What does `-t` do? What does `-r` do?
* What is the effect of `-p`?
* Why might sorting differ across machines?

**Tests:**

```sh
ls -mtp
ls -lrt
LC_ALL=C ls -mtp
```

**Keywords & Concepts:**

* **Locale**: influences sorting.
* **Collation**: order of characters.
* **Output formatting**: `-m` gives comma-separated list.

---

## ex05 — GiT commit

**You must know:**

* How to get the last 5 commit hashes.
* Difference between plumbing and porcelain commands.

**Defense questions:**

* What is SHA-1?
* What is the difference between `git log` and `git show`?
* How would you script extracting commits?

**Tests:**

```sh
git log -n5 --format=%H
git rev-parse HEAD
```

**Keywords & Concepts:**

* **Commit hash**: unique ID for commit.
* **HEAD**: reference to latest commit.
* **Rev-parse**: low-level git command.

---

## ex06 — gitignore

**You must know:**

* `.gitignore` syntax and patterns.
* Difference between ignored and untracked files.

**Defense questions:**

* Does `.gitignore` remove files already tracked?
* What is the effect of `!pattern`?
* What does `git check-ignore` do?

**Tests:**

```sh
echo "*.o" > .gitignore
git status
git ls-files --others -i --exclude-standard
```

**Keywords & Concepts:**

* **Glob patterns**: `*`, `?`, `**`.
* **Negation**: `!`.
* **Exclude-standard**: respects system ignores.

---

## ex07 — diff

**You must know:**

* How to compare two files.
* Different diff formats (unified, context).
* Patch application.

**Defense questions:**

* What do `+` and `-` mean in a diff?
* How do you apply a patch?
* What is exit status of `diff`?

**Tests:**

```sh
diff file1 file2
diff -u file1 file2 > file.patch
patch < file.patch
```

**Keywords & Concepts:**

* **Unified diff format**.
* **Patch**.
* **Whitespace sensitivity**.

---

## ex08 — clean

**You must know:**

* `find` command with predicates.
* How to delete files safely.

**Defense questions:**

* What’s the difference between `rm` and `rm -f`?
* How to prune `.git` folder?
* What is the difference between `-exec` and `-delete`?

**Tests:**

```sh
find . -type f \( -name '*~' -o -name '#*#' \) -print -delete
```

**Keywords & Concepts:**

* **find command**.
* **Prune**.
* **Glob vs regex** in find.

---

## ex09 — Illusions (Magic file)

**You must know:**

* Magic numbers and `file(1)` command.
* How to define offsets in a magic file.

**Defense questions:**

* What is the difference between offset 41 and “42nd byte”?
* What happens if the magic doesn’t match?
* How does `file -m` use your magic?

**Tests:**

```sh
xxd file
file -m ft_magic somefile
```

**Keywords & Concepts:**

* **Magic database**.
* **Offset** (0-based).
* **Type tests**: string, byte, short, etc.

---

# 🧰 Core Shell Concepts (for defense)

* **POSIX sh vs bash**: evaluators expect portable POSIX shell.
* **Redirections**: `>`, `>>`, `<`, `2>`, `2>&1`.
* **Quoting**: single quotes, double quotes, escaping.
* **Command substitution**: `$(...)` vs backticks.
* **Exit status**: `$?`, 0=success.
* **Globbing vs Regex**: wildcards vs regex.
* **Filesystem**: inode, permissions (octal vs symbolic), suid/sgid/sticky bits.
* **Timestamps**: atime, mtime, ctime.
* **Locale**: `LC_ALL=C` for consistent output.

