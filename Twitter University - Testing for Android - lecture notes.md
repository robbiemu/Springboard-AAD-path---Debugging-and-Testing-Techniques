#Testing for Android
## notes from video: https://www.youtube.com/watch?v=Od9l-OGAXC8

### Why test?

84% of users will look for a replacement after the second crash.

Automation in testing is useful in moderation. getting users out of the loop completely is a bad thing. particularly in:
* UX
* 


### Options:

* Android Studio — provides a strong unit testing framework. does not provide actual use feedback
* Emulator — provides a simulation that may work like real devices. does not provide actual device-based use feedback.
* Real devices — provides actual device-based results. there are thousands of devices though, for limited usefulness.

 QA professionals, necessary for large groups. con is that it is expensive

### Autmation

* autmoation is a software project (unto itself) - you'd need specs and a design plan to get there.
* automate is a tool, not a solution - you need to keep human eyes on output before selling things to end users
* automate with precision - fulfilling realistic user stories is a good pattern for automation
* it's all about data - use data to describe a large set of testable paths if the app is small, but focus for larger apps. instead identify critical paths
* abstraction - tests should pass off specific interfaces to intermediate classes, just like in your app.
  
### Tools

* Recorder - records user actions, humans pilot. then it can play back the path to test UI. Non-developers can use these. downside is they can create difficult to maintain, fragile scripts.
Best practice: use this to create/identify use-paths, and then use real scripting to test the results.
* UI Exerciser Monkey - stress testing from Android. easy to use
* Android Testing Framework - **Android** JUnit. serves as foundation for testing, as well as fullfilling unit tests
* UI Automater - **Android** JUnit.. extends the basic unit with UI selectors and manipulators. handles dialogs, etc. This is a solid testing framework for modern android (2016) 
* RoboElectic - add on that mocks system fnuctionality, runs in JVM. not a full system mock (basially not an emulator).

####Non-JVM

* Robotium - UI testing on top of normal andoird junit.
* Cucumber - It is ruby based/extenal. Calabash is an implentation. provies human readable interface to writing unit-test style tests. but can be rigged up to usage paths through behavior driven design.
* Appium - like Selenium. can write tests in pyhon, ruby, etc. runs on emulators and real devices. but it implements webdriver for testing, so there are testing components that dont really work (no cookies in an app, for example)
* Spoon — run instrumentation tests in parellel in real emulators/devices. produces graphic output at end fo run.

####Commercial

* well-supported
* geared to enterprise
* expensive, requires commitment

#### How to choose

* big teams with complex apps may want commericial support
* the built-in frameworks probably are sufficient or small scale projects.
* for automation and UI testing, at least free UI testing would make sense