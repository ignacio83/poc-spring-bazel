# poc-spring-bazel

```shell
bazel run @maven//:pin
bazel run //:gazelle
bazel build //src/main/java/com/afi/bazel/demo:DemoApplication_deploy.jar 
```

## Good points
* Gazelle works with Java

## Problems
* Spring Stack does not help with Bazel. 
* Tests must end with Test suffix or then add `test_suffixes = ["Tests.java"]` to java_suite_test.
* Must declare dependencies explicit.