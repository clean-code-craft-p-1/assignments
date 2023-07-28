
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

---

## Interesting Patterns

[Use of abstract base class](https://github.com/clean-code-craft-p-1/spring-in-cpp-Brahmaprasad/pull/1/files)

[...and using off-the-shelf functionality](https://github.com/clean-code-craft-p-1/spring-in-cpp-ThribhuvanGuptaS/blob/fa7dfe7319ebe163e113d40825ae24aebcdfbaa9/stats.cpp)

[Type flexibility via templates](https://github.com/clean-code-craft-p-1/spring-in-cpp-ShubhaPankaj/blob/fa004e7aaf2c2f9bacd5d0240d0eac98932fad19/stats.h)

[Explicitly disallow untested behavior](https://github.com/clean-code-craft-p-1/spring-in-cpp-ajaybth87/blob/413b535277eb0284b28017be51aabd06f3766b40/stats.h)
