# poc-spring-bazel

```shell
bazel run @maven//:pin
bazel run //:gazelle
```

## Good points
* Gazelle works

## Problems
* Spring Stack does not help with Bazel 
* Tests must end with Test suffix or then add `test_suffixes = ["Tests.java"]` to java_suite_test.
* Must declare dependencies explicit