# Proving your code

[Separation of proving-code from deliverables](https://github.com/clean-code-craft-p-1/test-failer-in-cpp-Sudarshan-CC)

[Example of alignment tests](https://github.com/clean-code-craft-p-1/test-failer-in-cpp-vikas-ph/blob/master/misaligned.cpp)

[Separation of formation](https://github.com/clean-code-craft-p-1/test-failer-in-cpp-ShubhaPankaj/blob/master/misaligned.cpp)

# Isolation helps

How many responsibilities are in this code?

```c
const char* majorColor[] = {"White", "Red", "Black", "Yellow", "Violet"};
const char* minorColor[] = {"Blue", "Orange", "Green", "Brown", "Slate"};
int i = 0, j = 0;
for(i = 0; i < 5; i++) {
    for(j = 0; j < 5; j++) {
        printf("%d | %s | %s\n", i * 5 + j, majorColor[i], minorColor[i]);
    }
}
```

Responsibilities of the above code:
- Language
- Sequence
- Index (`i` and `j`) to color translation
- Formatting
