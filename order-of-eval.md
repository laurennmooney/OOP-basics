## Order of Evaluation

### What is Order of Evaluation?

So, time to rewind to some programming basics, just in general: operations. You know, adding, substracting, multiplying, etc. 

Something I've never been certain of since learning standard arithmetic operations back in good ole vanilla Javascript is whether or not it followed the "Order of Operations." You know, PLEASE EXCUSE MY DEAR AUNT SALLY (PEMDAS). It was safe to assume yes, and I was right, but never knew if there was a specific rule-of-thumb followed for code.

Well, I got my answer, at least for C#, and its called **Order of Evaluation**, which has two factors to it:
- Operator Precedence
- Operator Associativity

### Precedence and Associativity Table:

| Symbol                            | Type of Operatioon | Associativity |
| --------------------------------- | ------------------ | ------------- |
| [ ] ( ) . -> ++ -- (postfix)      | Expression         | left to right |
| sizeof & * + - ~ ! ++ -- (prefix) | Unary              | right to left |
| * / %                             | Multiplicative     | left to right |
| + -                               | Additive           | left to right |
| = \*= /= += -= <<= >>= &= ^= \|=   | Simple and Compound Assignment | right to left | 

This is a shortened form of the table. There are a whole bunch of different operations that are included in Order of Evaluation.

In this table, the operators are listed in decending order of precedence. So operations in parentheses will be evaluated before the operation occurring outside of it.

**Example:**
```csharp
(3 + 4) * 2; // this will return 14 because 3 + 4 is calculated first, so 7 * 2 is 14.
```

What if you have operators that fall into the same precedence (same line in the table)? This is where associativity comes in. The operators will be evaluated in whatever direction specified. For example, * will be evaluated before /, and + before -, because both of these levels of precedence have an associatively that reads left to right. Notice that unary goes right to left though.

If you want to see the full table, you can go [here](https://www.tutorialspoint.com/csharp/csharp_operators_precedence.htm).

*(might add more but this is a pretty good intro to this..)*
