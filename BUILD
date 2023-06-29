java_binary(
  name = 'app',
  main_class = 'br.com.afi.bazel.demo.DemoApplication',
  srcs = glob(["src/main/java/**/*.java"]),
  resources = glob(["src/main/resources/**"]),
  deps = [
    '@maven//:org_springframework_boot_spring_boot_starter_actuator',
    '@maven//:org_springframework_boot_spring_boot_starter_web',
    '@maven//:org_springframework_boot_spring_boot_autoconfigure',
    '@maven//:org_springframework_boot_spring_boot',
  ],
)