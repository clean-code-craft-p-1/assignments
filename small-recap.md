# Small and well-named

Prove functionality with asserts?

```c
int pairNumber = TelCoColorCoder::GetPairNumberFromColor(major, minor);
assert(pairNumber == expectedPairNumber);
```

or prove by looking at the output?

`printRefManual();`

```
  Color Code Manual :  
----------------------------------------
| Pair No. | Major Color, Minor Color  |
----------------------------------------
| 1        | White, Blue               |
| 2        | White, Orange             |
| 3        | White, Green              |
| 4        | White, Brown              |
| 5        | White, Slate              |
| 6        | Red, Blue                 |
```

---

Avoid generic naming

- A filename like `utils.h` tends to collect unrelated functionality with successive releases

---

Added functionality in its own file

- https://github.com/clean-code-craft-p-1/well-named-in-cpp-ShubhaPankaj
- https://github.com/clean-code-craft-p-1/well-named-in-cpp-ajaybth87/pull/1/files
- https://github.com/clean-code-craft-p-1/well-named-in-cpp-ShubhaPankaj/pull/1/files

---

Keep related things together

[This header file](https://github.com/clean-code-craft-p-1/well-named-in-cpp-ThribhuvanGuptaS/blob/913d720a24792a0ada936e54bf93008ff6992508/TelCoColorCoderVars.h) defines enums. It's a good thing to separate it from functionality.
Constraint is - The array of names must have the same number of values as the number of enums. Assume another developer can make a mistake while adding a color.
Any way to catch this error early? At compile time? In unit-testing?
