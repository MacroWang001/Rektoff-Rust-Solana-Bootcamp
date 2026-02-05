## Ownership Quiz

This quiz covers your knowledge of ownership in Rust through **Ownership Set Notation**.  
The questions explore both **Lexical Lifetimes (LL)** and **Non-Lexical Lifetimes (NLL)**.

---

## Answer Format Guidelines

- **Letter/term answers**:  
  Just provide the letter or term – no comments or extra information.  
  Example: `A`, `mut x`.

- **Ownership sets**:  
  Provide only the set and its contents – no explanations before or after.  
  Example of what *to write*:  
  `main{mut a, b, block{}}`  
  Do **not** add `//` comments or extra text like `✅ x is in ownership set for main`.

- **Set construction**:  
  Add new terms to the **right** of the set and maintain order – do **not** shuffle.  
  Look at the analysis in the questions to see what this means.

- **Empty answers**:  
  If an answer should be empty, you **must** acknowledge that it is empty by writing `Empty`.  
  Leaving the field blank is **not** the same as acknowledging emptiness.

- **Error lines**:  
  When identifying an error in the analysis, prefix your answer with `ERROR: ` followed by the **prior state** that demonstrates the error.  
  Example:

```text
// main{}
let x = vec![1, 2, 3];
// main{x}
let y = x;
// main{y}
let z = x; // ERROR: main{y}
```

- **After an error**:  
  Analysis does not continue past an error.  
  For any answer fields after the error line, write `Empty` since the program would not reach that point.

Example:

```text
// main{}
let x = vec![1, 2, 3];
// main{x}
let y = x;
// main{y}
let z = x; // ERROR: main{y}
// Empty
let a = &y; // Empty
```

---

## Automated Feedback System

This quiz uses a simple **string matching algorithm** to provide instantaneous feedback on your answers.  
The automated system is designed to give you quick responses to help you evaluate and improve your understanding in real-time.

If you're confused by any feedback or believe there might be an error in the feedback, feel free to reach out for clarification. However, please also understand:

- Minor syntax variations or formatting differences might occur.
- These may show as incorrect in the automated feedback but will **not** be considered wrong for grading.
- The goal is to provide fast, helpful feedback you can review yourself rather than being overly strict about exact formatting.

Trust that you will be marked fairly.

---

## Important Warning

- **Answers are not saved**:  
  Any answers you enter will be lost if you refresh or close this page.  
  I recommend doing your work in a separate document (saved to disk) or on paper first, then copying your final answers into the form.

- **Feedback does not persist**:  
  After you submit, screenshot or copy the feedback if you want to keep it.  
  The feedback will disappear when you refresh or close the page.

Good luck!

---

## Question 1: Ownership – String

Here is some code and some **Lexical Lifetimes (LL)** notation, but it has an error.  
Answer the following:

- **A.** Provide the line number where the analysis first goes wrong (what line of notation).  
  - Make sure to verify all lines above your answer are correct as you are reporting the **earliest** error.
- **B.** For **Lexical Lifetime (LL)**, what should the **first element** of the `main` set of line 8 be?  i.e. `main{B, ...}` – what is `B`?
- **C.** For **Lexical Lifetime (LL)**, what should the **second element** of the `main` set of line 8 be?  i.e. `main{..., C}` – what is `C`?
- **D.** For **Non-Lexical Lifetime (NLL)**, what should the **first element** of the `main` set of line 12 be?  i.e. `main{D, ...}` – what is `D`?
- **E.** For **Non-Lexical Lifetime (NLL)**, what should the **second element** of the `main` set of line 12 be?  i.e. `main{..., E}` – what is `E`?

If an answer should be empty, you must acknowledge that it is empty by writing `Empty`.

```rust
fn main() {
    let mut s = String::from("hello");

    let r = &s;
    println!("{}", r);

    s.push_str(" world");
    println!("{}", s);
}
```

```text
1 fn main() {
2     // main{}
3     let mut s = String::from("hello");
4     // main{mut s}
5     let r = &s;
6     // main{mut s, r(&s)}
7     println!("{}", r); // main{mut s, r(&s)} ✅ r is in ownership set for main
8     // main{mut s, r(&s)}
9 
10     s.push_str(" world"); // main{mut s, r(&s), push_str{self(&mut s)}}
11     // main{mut s, r(&s)}
12     println!("{}", s); // main{mut s, r(&s)} ✅ s is in ownership set for main
13     // main{mut s, r(&s)}
14 } // nothing - main ends, s and r are dropped by LL
```

- **Answer for A**  
  Your answer: `__________`

- **Answer for B**  
  Your answer: `__________`

- **Answer for C**  
  Your answer: `__________`

- **Answer for D**  
  Your answer: `__________`

- **Answer for E**  
  Your answer: `__________`

- **Additional comments** (optional, not graded) ： 

---

## Question 2: Ownership – Control Flow

Here is some code and some **Lexical Lifetimes (LL)** notation, but it has an error.  
Answer the following:

- **A.** Provide the line number where the analysis first goes wrong (what line of notation).  
  - Make sure to verify all lines above your answer are correct as you are reporting the earliest error.

Then provide the **correct sets** for the following lines:

- **LL.6** – Correct **Lexical Lifetimes (LL)** set for line 6.  
- **NLL.6** – Correct **Non-Lexical Lifetimes (NLL)** set for line 6.  
- **LL.9** – Correct **Lexical Lifetimes (LL)** set for line 9.  
- **NLL.9** – Correct **Non-Lexical Lifetimes (NLL)** set for line 9.  
- **LL.11** – Correct **Lexical Lifetimes (LL)** set for line 11.  
- **NLL.11** – Correct **Non-Lexical Lifetimes (NLL)** set for line 11.  
- **LL.13** – Correct **Lexical Lifetimes (LL)** set for line 13.  
- **NLL.13** – Correct **Non-Lexical Lifetimes (NLL)** set for line 13.  
- **LL.14** – Correct **Lexical Lifetimes (LL)** set for line 14.  
- **NLL.14** – Correct **Non-Lexical Lifetimes (NLL)** set for line 14.  
- **LL.15** – Correct **Lexical Lifetimes (LL)** set for line 15.  
- **NLL.15** – Correct **Non-Lexical Lifetimes (NLL)** set for line 15.  
- **LL.17** – Correct **Lexical Lifetimes (LL)** set for line 17.  
- **NLL.17** – Correct **Non-Lexical Lifetimes (NLL)** set for line 17.  
- **LL.18** – Correct **Lexical Lifetimes (LL)** set for line 18.  
- **NLL.18** – Correct **Non-Lexical Lifetimes (NLL)** set for line 18.  
- **LL.19** – Correct **Lexical Lifetimes (LL)** set for line 19.  
- **NLL.19** – Correct **Non-Lexical Lifetimes (NLL)** set for line 19.  
- **LL.22** – Correct **Lexical Lifetimes (LL)** set for line 22.  
- **NLL.22** – Correct **Non-Lexical Lifetimes (NLL)** set for line 22.

If an answer should be empty, you must acknowledge that it is empty by writing `Empty`.


```rust
fn main() {
    let mut x = 5;
    let y = &x;
    
    if true {
        println!("{}", y);
    } else {
        let z = &mut x;
        *z += 1;
    }
    println!("{}", x);
}
```

```text
1 fn main() {
2     // main{}
3     let mut x = 5;
4     // main{mut x}
5     let y = &x;
6     // main{shr x, y(&x)}
7    
8     if true {
9         // main{shr x, y(&x), if{}}
10        println!("{}", y); // main{shr x, y(&x), if{}} ✅ y is in ownership set for main
11        // main{shr x, y(&x), if{}}
12    } else {
13        // main{shr x, y(&x), else{}}
14        let z = &mut x; // main{shr x, y(&x), else{z(&mut x)}} ✅ y is in ownership set for main and x isn't frz
15        // main{frz x, y(&x), else{z(&mut x)}}
16
17        *z += 1; // main{frz x, y(&x), else{z(&mut x)}} ✅ z is in ownership set for main and is &mut
18        // main{frz x, y(&x), else{z(&mut x)}}
19    } // main{mut x, y(&x)} - if and else frames are dropped by LL, x restored to mut
20
21    println!("{}", x); // main{mut x, y(&x)} ✅ x is in ownership set for main
22    // main{mut x, y(&x)}
23} // nothing - main ends, x and y are dropped by LL
```

- **Answer for A**  
  Your answer: `__________`

- **Answer for LL.6**  
  Your answer: `__________`

- **Answer for NLL.6**  
  Your answer: `__________`

- **Answer for LL.9**  
  Your answer: `__________`

- **Answer for NLL.9**  
  Your answer: `__________`

- **Answer for LL.11**  
  Your answer: `__________`

- **Answer for NLL.11**  
  Your answer: `__________`

- **Answer for LL.13**  
  Your answer: `__________`

- **Answer for NLL.13**  
  Your answer: `__________`

- **Answer for LL.14**  
  Your answer: `__________`

- **Answer for NLL.14**  
  Your answer: `__________`

- **Answer for LL.15**  
  Your answer: `__________`

- **Answer for NLL.15**  
  Your answer: `__________`

- **Answer for LL.17**  
  Your answer: `__________`

- **Answer for NLL.17**  
  Your answer: `__________`

- **Answer for LL.18**  
  Your answer: `__________`

- **Answer for NLL.18**  
  Your answer: `__________`

- **Answer for LL.19**  
  Your answer: `__________`

- **Answer for NLL.19**  
  Your answer: `__________`

- **Answer for LL.22**  
  Your answer: `__________`

- **Answer for NLL.22**  
  Your answer: `__________`

- **Additional comments** (optional, not graded) ： 

---

## Question 3: Ownership – Uninitialised Variables

This program won't compile with either the modern compiler (**NLL**) or the older compiler (**LL**).  
Here are (incorrect) ownership notations for both that don't show the error.

**Which description best describes the real reason the program won't compile and the analysis is wrong?**

- **A.** Ownership is a relation between variables to data, an uninitialised variable has no data and so does not own anything and cannot be added to the ownership set.
- **B.** Every declared variable has a slot in memory, so it counts as owned by the scope even before initialisation. The issue is not ownership, but trying to access the memory before a valid value is written.
- **C.** Uninitialised variables are still part of the ownership set but point to undefined data until first use. Printing `x` is fine because it just prints an undefined `Vec` handle, not the data itself.
- **D.** Ownership is a runtime concept, so analysing it before execution is always incomplete. Since `x` isn't used yet, there's no way to know about runtime memory.

Please just answer with `A`, `B`, `C`, or `D`.


```rust
fn main() {
    let x: Vec<i32>;
    println!("{:?}", x);
}
```

```text
fn main() {
    // main{}
    let x: Vec<i32>;
    // main{x}
    println!("{:?}", x); // ✅ x is in ownership set for main
    // main{x}
} // nothing - main ends, x is dropped by LL
```

```text
fn main() {
    // main{}
    let x: Vec<i32>;
    // main{x}
    println!("{:?}", x); // ✅ x is in ownership set for main
    // main{} <-- x is dropped by NLL
} // nothing, main frame is popped
```

- **Answer for Q3**  
  Your answer: `__________`

- **Additional comments** (optional, not graded) ： 


---

## Question 4: What Error is Ownership Preventing Here?

The Rust ownership model is preventing a memory error here.  
Imagine what would happen if the line with the comment were allowed to run.  
Look up and understand the error that Rust blocks in this snippet.

**What is the name of the common memory error that would occur here?**


```rust
fn main() {
    let x = vec![1, 2];
    drop(x);
    drop(x); // x cannot be passed as an arg as it was dropped above
    println!("{:?}", x);
}
```

- **Answer for Q4**  
  Your answer: `__________`

- **Additional comments** (optional, not graded) ： 

---

## Question 5: Ownership – Analysis of Threat

This code will not compile.

### Part 1

What is the basic principle Rust enforces to provide memory safety that is being violated?

- **A.** Exclusive Ownership  
- **B.** Aliasing XOR Mutability

### Part 2

Does this code present a real threat to memory safety?  
Answer `Yes` or `No` – but also add your reasoning in the comment section.

```rust
fn main() {
    let mut arr = [1, 2, 3];

    let a = &mut arr[0];
    let b = &mut arr[1];

    *a += 1;
    *b += 1;
}
```

- **Answer for Part 1**  
  Your answer: `__________`

- **Answer for Part 2**  
  Your answer: `__________`

- **Additional comments** (optional, not graded)  ：

