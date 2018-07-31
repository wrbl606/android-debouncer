# Android debouncer

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/wrbl606/android-debouncer/master/LICENSE)
[![Version](https://api.bintray.com/packages/wrbl606/maven/debouncer/images/download.svg) ](https://bintray.com/wrbl606/maven/android-debouncer/_latestVersion)
[![Minimum API](https://img.shields.io/badge/API-17%2B-blue.svg?style=flat)](https://android-arsenal.com/api?level=17)

Clean and simple solution for debouncing UI tasks (or any other).

* Min SDK: 17 (JELLY_BEAN_MR1)
* Footprint: Nearly none ♥

## Implementation
Insert this into your `build.gradle` file:
```gradle
    implementation 'com.github.wrbl606:android-debouncer:1.0'
```
and you are ready to go.

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
