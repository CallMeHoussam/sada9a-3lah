# 42 Piscine — C01 Full Preparation Guide

### **Ex00 – ft\_ft**

**Goal:** Write a function that takes a pointer to int and sets it to `42`.

* ❓ **Defense Questions**

  * What is a pointer?
  * What is the difference between `*nbr` and `nbr`?
  * Why `42`? (42 school joke).

* 🧠 **Algorithm**

  * Take `int *nbr`.
  * Dereference it: `*nbr = 42`.

* 🔑 **Keywords & Concepts**

  * Pointer basics.
  * Dereferencing.

* 📌 **You must know**

  * Memory vs. value.

* 🧪 **Tests**

  ```c
  int a;
  ft_ft(&a);
  printf("%d", a); // 42
  ```

---

### **Ex01 – ft\_ultimate\_ft**

**Goal:** Set `42` using 9 levels of pointers.

* ❓ **Defense Questions**

  * What is `*********nbr`?
  * How many levels of indirection are possible in C?
  * What’s the purpose of this exercise? (Understand deep pointers).

* 🧠 **Algorithm**

  * Dereference 9 times: `*********nbr = 42`.

* 🔑 **Keywords & Concepts**

  * Multi-level pointers.
  * Pointer to pointer.

* 📌 **You must know**

  * In memory, each level points to another address.

* 🧪 **Tests**

  ```c
  int a;
  int *p1 = &a; int **p2 = &p1; ... int *********p9 = &p8;
  ft_ultimate_ft(p9);
  printf("%d", a); // 42
  ```

---

### **Ex02 – ft\_swap**

**Goal:** Swap two integers.

* ❓ **Defense Questions**

  * Why use a temporary variable?
  * Can you swap without a temp variable?

* 🧠 **Algorithm**

  * Store `*a` in temp.
  * Assign `*a = *b`.
  * Assign `*b = temp`.

* 🔑 **Keywords & Concepts**

  * Passing by address.
  * Swapping techniques.

* 📌 **You must know**

  * Difference between swap with temp vs. arithmetic swap.

* 🧪 **Tests**

  ```c
  int x=5, y=10;
  ft_swap(&x, &y);
  // x=10, y=5
  ```

---

### **Ex03 – ft\_div\_mod**

**Goal:** Store division and modulo of `a / b`.

* ❓ **Defense Questions**

  * What happens if `b=0`?
  * What is the difference between `/` and `%` in C?

* 🧠 **Algorithm**

  * `*div = a / b;`
  * `*mod = a % b;`

* 🔑 **Keywords & Concepts**

  * Integer division.
  * Remainder operator.

* 📌 **You must know**

  * Division by zero is undefined.

* 🧪 **Tests**

  ```c
  int d, m;
  ft_div_mod(10, 3, &d, &m);
  // d=3, m=1
  ```

---

### **Ex04 – ft\_ultimate\_div\_mod**

**Goal:** Modify values directly (`a = a/b`, `b = a%b`).

* ❓ **Defense Questions**

  * Why do we use pointers instead of return?
  * What’s the difference with Ex03?

* 🧠 **Algorithm**

  * Save temp = \*a.
  * `*a = temp / *b;`
  * `*b = temp % *b;`

* 🔑 **Keywords & Concepts**

  * In-place modification.

* 📌 **You must know**

  * Pointers allow direct modification.

* 🧪 **Tests**

  ```c
  int a=10, b=3;
  ft_ultimate_div_mod(&a, &b);
  // a=3, b=1
  ```

---

### **Ex05 – ft\_putstr**

**Goal:** Print a string with `write`.

* ❓ **Defense Questions**

  * What is a string in C?
  * How does `write` know where a string ends?
  * Why `'\0'` is important?

* 🧠 **Algorithm**

  * While `str[i] != '\0'`, print char by char.

* 🔑 **Keywords & Concepts**

  * Strings in C = array of chars ending with `'\0'`.

* 📌 **You must know**

  * No `printf`, only `write`.

* 🧪 **Tests**

  ```c
  ft_putstr("Hello 1337!");
  // Hello 1337!
  ```

---

### **Ex06 – ft\_strlen**

**Goal:** Count string length.

* ❓ **Defense Questions**

  * How does strlen work internally?
  * Why stop at `'\0'`?

* 🧠 **Algorithm**

  * Initialize counter=0.
  * While `str[i] != '\0'`, increment counter.
  * Return counter.

* 🔑 **Keywords & Concepts**

  * Null-terminated strings.

* 📌 **You must know**

  * Difference between allocated size and strlen.

* 🧪 **Tests**

  ```c
  printf("%d", ft_strlen("42")); // 2
  ```

---

### **Ex07 – ft\_rev\_int\_tab**

**Goal:** Reverse an array of integers.

* ❓ **Defense Questions**

  * How to swap first and last?
  * What is the complexity of this algorithm?

* 🧠 **Algorithm**

  * For i=0 → size/2: swap tab\[i] and tab\[size-1-i].

* 🔑 **Keywords & Concepts**

  * Arrays and indexes.
  * Symmetry in reversal.

* 📌 **You must know**

  * Complexity = O(n/2).

* 🧪 **Tests**

  ```c
  int arr[5]={1,2,3,4,5};
  ft_rev_int_tab(arr,5);
  // arr = 5,4,3,2,1
  ```

---

### **Ex08 – ft\_sort\_int\_tab**

**Goal:** Sort an int array ascending.

* ❓ **Defense Questions**

  * What sorting algorithms do you know?
  * What’s the complexity of Bubble sort?

* 🧠 **Algorithm** (bubble sort style)

  * For i=0→size-1

    * For j=0→size-i-1

      * If tab\[j] > tab\[j+1] → swap.

* 🔑 **Keywords & Concepts**

  * Sorting algorithms.
  * Time complexity.

* 📌 **You must know**

  * Bubble sort = O(n²).

* 🧪 **Tests**

  ```c
  int arr[5]={5,3,1,4,2};
  ft_sort_int_tab(arr,5);
  // arr = 1,2,3,4,5
  ```
