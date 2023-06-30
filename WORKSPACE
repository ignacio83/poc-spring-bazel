load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

RULES_PROTO_VERSION = "5.3.0-21.7"

http_archive(
    name = "rules_proto",
    canonical_id = "https://github.com/bazelbuild/rules_proto/archive/refs/tags/{0}.tar.gz".format(RULES_PROTO_VERSION),
    sha256 = "dc3fb206a2cb3441b485eb1e423165b231235a1ea9b031b4433cf7bc1fa460dd",
    strip_prefix = "rules_proto-{0}".format(RULES_PROTO_VERSION),
    urls = [
        "https://github.com/bazelbuild/rules_proto/archive/refs/tags/{0}.tar.gz".format(RULES_PROTO_VERSION),
    ],
)

# register proto dependencies and toolchains
load("@rules_proto//proto:repositories.bzl", "rules_proto_dependencies", "rules_proto_toolchains")

rules_proto_dependencies()

rules_proto_toolchains()

http_archive(
    name = "io_bazel_rules_go",
    sha256 = "6dc2da7ab4cf5d7bfc7c949776b1b7c733f05e56edc4bcd9022bb249d2e2a996",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_go/releases/download/v0.39.1/rules_go-v0.39.1.zip",
        "https://github.com/bazelbuild/rules_go/releases/download/v0.39.1/rules_go-v0.39.1.zip",
    ],
)

load("@io_bazel_rules_go//go:deps.bzl", "go_register_toolchains", "go_rules_dependencies")

############################################################
# Define your own dependencies here using go_repository.
# Else, dependencies declared by rules_go/gazelle will be used.
# The first declaration of an external repository "wins".
############################################################

go_rules_dependencies()

go_register_toolchains(version = "1.20.4")

http_archive(
    name = "bazel_gazelle",
    sha256 = "727f3e4edd96ea20c29e8c2ca9e8d2af724d8c7778e7923a854b2c80952bc405",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/bazel-gazelle/releases/download/v0.31.1/bazel-gazelle-v0.31.1.tar.gz",
        "https://github.com/bazelbuild/bazel-gazelle/releases/download/v0.31.1/bazel-gazelle-v0.31.1.tar.gz",
    ],
)

load("@bazel_gazelle//:deps.bzl", "gazelle_dependencies", "go_repository")

gazelle_dependencies()

http_archive(
    name = "contrib_rules_jvm",
    sha256 = "2b710518847279f655a18a51a1629b033e4406f29609e73eb07ecfb6f0138d25",
    strip_prefix = "rules_jvm-0.13.0",
    url = "https://github.com/bazel-contrib/rules_jvm/releases/download/v0.13.0/rules_jvm-v0.13.0.tar.gz",
)

load("@contrib_rules_jvm//:repositories.bzl", "contrib_rules_jvm_deps", "contrib_rules_jvm_gazelle_deps")

contrib_rules_jvm_deps()

contrib_rules_jvm_gazelle_deps()

# Now ensure that the downloaded deps are properly configured
load("@contrib_rules_jvm//:setup.bzl", "contrib_rules_jvm_setup")

contrib_rules_jvm_setup()

load("@contrib_rules_jvm//:gazelle_setup.bzl", "contrib_rules_jvm_gazelle_setup")

contrib_rules_jvm_gazelle_setup()

RULES_JVM_EXTERNAL_TAG = "4.3"
RULES_JVM_EXTERNAL_SHA = "6274687f6fc5783b589f56a2f1ed60de3ce1f99bc4e8f9edef3de43bdf7c6e74"

http_archive(
    name = "rules_jvm_external",
    sha256 = RULES_JVM_EXTERNAL_SHA,
    strip_prefix = "rules_jvm_external-%s" % RULES_JVM_EXTERNAL_TAG,
    url = "https://github.com/bazelbuild/rules_jvm_external/archive/%s.zip" % RULES_JVM_EXTERNAL_TAG,
)

load("@rules_jvm_external//:defs.bzl", "maven_install")

JUNIT_JUPITER_VERSION = "5.9.3"
JUNIT_PLATFORM_VERSION = "1.9.3"
SPRING_BOOT_VERSION = "3.1.1"

maven_install(
  artifacts = [
    "org.springframework.boot:spring-boot-autoconfigure:%s" % SPRING_BOOT_VERSION,
    "org.springframework.boot:spring-boot-starter-web:%s" % SPRING_BOOT_VERSION,
    "org.springframework.boot:spring-boot-starter-actuator:%s" % SPRING_BOOT_VERSION,
    "org.springframework.boot:spring-boot-starter-test:%s" % SPRING_BOOT_VERSION,
    "org.springframework.boot:spring-boot-test:%s" % SPRING_BOOT_VERSION,
    "org.springframework:spring-test:6.0.10",
    "org.junit.platform:junit-platform-launcher:%s" % JUNIT_PLATFORM_VERSION,
    "org.junit.platform:junit-platform-reporting:%s" % JUNIT_PLATFORM_VERSION,
    "org.junit.jupiter:junit-jupiter-api:%s" % JUNIT_JUPITER_VERSION,
    "org.junit.jupiter:junit-jupiter-params:%s" % JUNIT_JUPITER_VERSION,
    "org.junit.jupiter:junit-jupiter-engine:%s" % JUNIT_JUPITER_VERSION,
  ],
  repositories = [
    'https://repo1.maven.org/maven2',
  ],
)