# Extensions

[Open to add languages](https://github.com/clean-code-craft-p-1/simple-monitor-in-cpp-ajaybth87/blob/cea1dcd57ece437f8a46a628bb009269a875d93b/Language.cpp)

[Testing the whole and the parts](https://github.com/clean-code-craft-p-1/simple-monitor-in-cpp-vikas-ph/blob/06918403b069b8dc42d5d6a0d3a0c61846dbe231/testMain.cpp)

[Refactoring to be open for ranges](https://github.com/clean-code-craft-p-1/simple-monitor-in-cpp-Rahul-P463/blob/ec137cec1e8ba1c7a8c0527c24cd08161e4fd02c/checker.cpp)

---

[Convert inside check](https://github.com/clean-code-craft-p-1/simple-monitor-in-cpp-Prateek-Wayne/blob/2b38321a25de323250c2a07c7146bea618168b2c/checker.cpp#L45)...?

```c
float convertTemperature(float temperature, string unit) {
    if (unit == "Celsius") {
        temperature = temperature * 9/5 + 32;
    }
    return temperature;
}

bool checkTemperature(float temperature, string unit = "Fahrenheit") {
    // Convert temperature to Fahrenheit if unit is "Celsius"
    
    if (isTemperatureCritical(temperature)) {
        printCriticalMessage("Temperature critical!");
        return false;
    }
    return true;
}

bool temperatureIsOk = checkTemperature(float temperature);
```

...or convert and then check?

```c

    temperature = convertTemperature(temperature, unit);
    bool temperatureIsOk = checkTemperature(float temperature);
```

---

