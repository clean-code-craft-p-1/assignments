# Failing tests

What is an assert?

```c
    assert(size(42)=='L');
    assert(size(42)=='M');
```

Watch the asserts: Is this a single requirement?

```c
void TestRainy()
{
    SensorStub sensor;
    string report = Report(sensor);
    assert(report.find("rain") != string::npos);
}

void TestHighPrecipitation()
{
    HighPrecipitationSensorStub sensor;
    string report = Report(sensor);
    assert(report.find("rain") != string::npos);
}
```

---

Duplication in formatting

```c
if (calculateColor(i, j) < 10)
{
    cout << calculateColor(i, j) << " "
            << " | " << setw(7) << majorColor[i]
            << setw(5) << " | " << minorColor[i] << "\n";
}
else
{
    cout << calculateColor(i, j)
            << " | " << setw(7) << majorColor[i]
            << setw(5) << " | " << minorColor[i] << "\n";
}
```

---

[Is it hard to test for alignment?](https://github.com/clean-code-craft-p-1/test-failer-in-cpp-vikas-ph/blob/099ee4979a29d9537320f999042b0d07be2e01b0/misaligned.cpp)
What do we do about it?

---

Interesting repos:

[Simple asserts for alignment](https://github.com/clean-code-craft-p-1/test-failer-in-py-prasadpn/blob/f0287c2f1824062c07ee8dcff119aaa396fb959a/misaligned.py)

[Parametrized stubs to reduce code](https://github.com/clean-code-craft-p-1/test-failer-in-cpp-vikas-ph/blob/099ee4979a29d9537320f999042b0d07be2e01b0/weatherreport.cpp)
