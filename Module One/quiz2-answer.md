## Q1:
Answer for A: 6

Answer for B: shr s

Answer for C: r(&s)

Answer for D: mut s

Answer for E: Empty


## Q2:

Answer for A: 14

Answer for LL.6: main{shr x, y(&x)}

Answer for NLL.6: main{shr x, y(&x)}

Answer for LL.9: main{shr x, y(&x), if{}}

Answer for NLL.9: main{shr x, y(&x), if{}}

Answer for LL.11: main{shr x, y(&x), if{}}

Answer for NLL.11: main{mut x, if{}}

Answer for LL.13: main{shr x, y(&x), else{}}

Answer for NLL.13: main{mut x, else{}}

Answer for LL.14: ERROR: main{shr x, y(&x), else{}}

Answer for NLL.14: main{frz x, else{z(&mut x)}}

Answer for LL.15: Empty

Answer for NLL.15: main{frz x, else{z(&mut x)}}

Answer for LL.17: Empty

Answer for NLL.17: main{frz x, else{z(&mut x)}}

Answer for LL.18: Empty

Answer for NLL.18: main{mut x, else{}}

Answer for LL.19: Empty

Answer for NLL.19: main{mut x}

Answer for LL.22: Empty

Answer for NLL.22: main{}


## Q3:

Answer for Q3: A

Additional comments (optional, not graded): Ownership tracks the relationship between variables and the data they own. An uninitialized variable has no data, so it owns nothing and shouldn't be in the ownership set. The analyses are wrong to add x to main{x} after just the declaration. It should remain main{} until x is actually initialized with data.



## Q4:

Double Free;

The first drop(x) deallocates the heap memory owned by the Vec. If the second drop(x) were allowed, it would attempt to free the same memory again (double free). The println would be a use-after-free. Rust's exclusive ownership makes it impossible to accidentally access memory that’s already been freed — at least through moves like this. 


## Q5: 
 
Answer for Part1: B

Answer for Part2: No

Additional comments here: This does not present a real threat to memory safety. The two mutable references point to different array elements (arr[0] and arr[1]), so they don't actually alias the same memory.    The borrow checker is conservative and rejects this safe code because it treats the entire array as borrowed rather than tracking individual element borrows.












