# Android debouncer

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/xolan/android-debouncer/master/LICENSE)
[![Master](https://img.shields.io/travis/xolan/android-debouncer/master.svg)](https://travis-ci.org/xolan/android-debouncer.svg?branch=master)

Clean and simple solution for debouncing UI tasks (or any other).

* Min SDK: 17 (JELLY_BEAN_MR1)
* Footprint: Nearly none ♥

## Usage

All you need to do is provide a unique identifier for your task. The task itself should be passed as `Runnable`.
The last parameter is debounce delay (in milliseconds).

### Example:
```java
Debouncer.debounce("example-task", new Runnable() {
    @Override
    public void run() {
        // Will not be ran due to the call below
        ...
    }
}, 250);

Thread.sleep(100, 0);

Debouncer.debounce("example-task", new Runnable() {
    @Override
    public void run() {
        // Overrides the previous call with identifier "example-task", running after approx. 350ms.
        // 100ms simulated "wait" time, 250ms debounce time.
        ...
    }
}, 250);
```
