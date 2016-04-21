# Debugging & Testing Your Android Applications 
## notes from youtube video: https://www.youtube.com/watch?v=AJVolvNwHL8

_see also: [Automated Performance Testing Codelab](https://codelabs.developers.google.com/codelabs/android-perf-testing/index.html?index=..%2F..%2Findex#0) from Google_

### Common tools we will explore

* logcat
* debugger
* traceview
* hierarchyViewer

### Debugging tools

#### Logcat

* logcat can be run from the commandline via `adb logcat`
* specify filter at end like `myapp:*`
* specify all others Silent with ` *:S` after the filter
* logcat is kernel native, available to any code that runs on the system.

#### Debugger

* works like any other debugger
* can run to cursor, which is nice

#### TraceView

pulls a full trace during the run of the app. 

start with `Debug.startMethodTracing` like in oncreate, and likewise close it onstop.

I believe it now works differently. It is part of Andorid studio, and it works without capturing. Produces system graphs, etc.

#### HierarchyViewer

Ships with studio, under adm / Hierarchy view. You can see the views and viewgroups hierarchy (including implicit views you may not realize). It can help in optimizing UI.

* Use this tool to shorten depth: You want a breadth spread, not a deep tree.
* there are (or at least were) dots that attach to views when active, showing if there are items with red dots an issue with the view getting enough time or something to that nature (some optmization is needed to get out of the way of the ui).

This tool can be used for other apps running on the emulator/device as well.

### Testing

* Android JUnit - these are made for you automatically now. spearate package, same namespace, junit preloaded into new classes in the package.
* Monkey Runner

_see also: [Developing Android unit and instrumentation tests - Tutorial](http://www.vogella.com/tutorials/AndroidTesting/article.html) for a version of UI testing on Android Studio_

#### JUnit
_tl;dr - unit tests can be done for the ui (acitivties/fragments) with mocks_

* AndroidTestCase was the base class - import org.junit.Test; now. Annotation provided includes @Test which marks a void method thowing Exception as a test in the object.
* Use asserts to pass/fail the test. Custom view asserts: assertGroupContains/NotContains, assertHasScreenCoordinates, assertOnScreen, assertOffScreenAbove/Below
* If you want to JUnit-test your UI (instead of just human-verification/automation testing) You can use mock objects (Mockito is the common solution) ..allows you to mock/fake objects that are necesasary for the test.

This test can trigger changes at different elements in succession: it , a use-case path.

### On-Emulator/Device testing:

#### Monkey

* start with something like `adb shell monkey N` where N is the number of milliseconds monkey has to stress test your UI.
* triggers random possible UI events.
* with -p com.packagename.package to test only your app's UI elements
* if it gneerates a crahs, you get a seed that you can retest with monkey to see if the same use-case is fixed after you make changes.

#### Monkeyrunner, et al

* very scriptable python api (possibly more now)

Robotium is another scriptiable UI testing system
Selenium is a generic testing app like this, and is a defacto qa system

(also Espresso)