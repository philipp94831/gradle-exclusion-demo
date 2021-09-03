# gradle-exclusion-demo

The following command fails with Gradle 6.8.x because of a failing test:

```
$ ./gradlew wrapper --gradle-version 6.8.3 --distribution-type all
$ ./gradlew release -x test -Prelease.useAutomaticVersion=true --info

> Task :gradle-exclusion:gradle-exclusion:test FAILED

FakeTest > test() FAILED
    org.opentest4j.AssertionFailedError at FakeTest.java:9

1 test completed, 1 failed

> Task :gradle-exclusion:runBuildTasks FAILED

> Task :release FAILED
Release process failed, reverting back any changes made by Release Plugin.

FAILURE: Build failed with an exception.
```

If you switch to Gradle 6.7.x, everything works as expected because tests are properly excluded:

```
$ ./gradlew wrapper --gradle-version 6.7.1 --distribution-type all
$ ./gradlew release -x test -Prelease.useAutomaticVersion=true --info

BUILD SUCCESSFUL in 2s
1 actionable task: 1 executed
```
