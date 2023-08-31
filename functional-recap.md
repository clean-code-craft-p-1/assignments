# Reducing complexity

```c
int vitalsOk(float temperature, float pulseRate, float spo2) {
  if(temperature > 102 || temperature < 95) {
    ...
  } else if(pulseRate < 60 || pulseRate > 100) {
    ...
  } else if(spo2 < 90) {
    ...
  }
```

The function `vitalsOk` does many things:
- compare with limits
- multiple vitals
- print the breach
- overall conclusion

## Extract method

Each vital in its own function?

`bool checkTemperature(float temperature)`

`bool checkPulseRate(float pulseRate)`

`bool checkSpo2(float spo2)`

---

Or extract the abstractions?

`IsInRange(float vital, float upper, float lower)`

`ShowMessage(messageid)`

`DisplayCritical()`

## Naming on purpose

Classifying temperature

`bool checkTemperature(float temperature)`
or
`bool TemperatureIsOk(float temperature)`

---

Showing the criticality of the message

[Evolving names](https://github.com/clean-code-craft-p-1/simple-monitor-in-cpp-Rahul-P463/blob/714758268bb101ded35d29be98f48cdc18aa8da4/checker.cpp)

```c
void Sleep() {
  for (int i = 0; i < 6; i++) {
    cout << "\r* " << flush;
    sleep(1);
    cout << "\r *" << flush;
    sleep(1);
  }
}
```
or
```c
void getAttention() {
  for (int i = 0; i < 6; i++) {
    cout << "\r* " << flush;
    sleep(1);
    cout << "\r *" << flush;
    sleep(1);
  }
}```
