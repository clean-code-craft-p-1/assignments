
Do not create additional branches. Work directly on the accepted repository

---

What can be improved in this code?

```c
void check_and_alert(float maxThreshold, void (*alerter_funcptr[])(), Stats computedStats)
{
    int i=0;
    bool result = false;
    if(computedStats.max > maxThreshold) {
        for(i=0; i<2; i++) {
            (*alerter_funcptr[i])();
        }
    }
}
```

**Discussion**:
- The variable `result` is not used. It can be removed
- Naming of `i` can be more specific, like `alerter_index`
- Magic number `2` in the for loop can go by the size of the array instead (needs to be passed explicitly in C)
- Prefer to use pre-increment. It is faster, especially with complex types (overloading). Pre-increment doesn't need to evaluate to the original value.
- The name of the function reflects its implementation (check and alert). It doesn't convey the purpose of the function.

> What kind of name would convey the purpose? What else do you have to know, to improve the name?

---

Consider one file with the interface and variants. Any way to separate them?

```cpp
class IAlerter
{
public:
    virtual void sendAlert() = 0;
};

class EmailAlert : public IAlerter
{
public:
    bool emailSent = false;
public:
    virtual void sendAlert() override;
};

class LEDAlert : public IAlerter
{
public:
    bool ledGlows = false;
public:
    virtual void sendAlert() override;
};
```

**Discussion**:

- Placing all these classes in a single file makes it hard for multiple developers to add alerters
- Not having any concrete implementation means the interface is left hanging (no guidance on how to implement it)

> Always deliver interfaces with a stub or a mock, or a sample implementation with tests. It reduces ambiguity while trouble-shooting.

---

Passes the test. But when does it fail?

```cpp
template <typename T> T FindAverage(const std::vector<T>& vec) {
    T sum = std::accumulate(vec.begin(), vec.end(), 0.0);
    if (sum == 0)
        return NAN;
    else
        return sum / static_cast<double>(vec.size());
}
```

**Discussion**:

- The code makes good use of standard functionality. Good for both readability and prove-ability
- When the vector is empty, `sum` is zero and the function returns NAN as expected. However, if a bunch of zeros is given in the input `vec`, it still gives NAN. 

> Checking `if (vec.empty())` is closer to the requiement _return NAN if the input is empty_. Always choose the code structure that's closer to the real requirement.

---

## Interesting Patterns

[Use of abstract base class](https://github.com/clean-code-craft-p-1/spring-in-cpp-Brahmaprasad/pull/1/files)

[...and using off-the-shelf functionality](https://github.com/clean-code-craft-p-1/spring-in-cpp-ThribhuvanGuptaS/blob/fa7dfe7319ebe163e113d40825ae24aebcdfbaa9/stats.cpp)

[Type flexibility via templates](https://github.com/clean-code-craft-p-1/spring-in-cpp-ShubhaPankaj/blob/fa004e7aaf2c2f9bacd5d0240d0eac98932fad19/stats.h)

[Explicitly disallow untested behavior](https://github.com/clean-code-craft-p-1/spring-in-cpp-ajaybth87/blob/413b535277eb0284b28017be51aabd06f3766b40/stats.h)
