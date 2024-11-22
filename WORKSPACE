load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

_COMPOSE_VERSION = "1.2.1"

_COMPOSE_COMPILER_VERSION = "1.5.9"

_KOTLIN_COMPILER_VERSION = "1.9.22"

_KOTLIN_COMPILER_SHA = "88b39213506532c816ff56348c07bbeefe0c8d18943bffbad11063cf97cac3e6"

_ANDROID_VERSION = "0.1.1"

_ANDROID_SHA = "cd06d15dd8bb59926e4d65f9003bfc20f9da4b2519985c27e190cddc8b7a7806"

_SKYLIB_VERSION = "1.4.2"

_SKYLIB_SHA = "66ffd9315665bfaafc96b52278f57c7e2dd09f5ede279ea6d39b2be471e7e3aa"

_RULES_JVM_EXTERNAL_TAG = "5.3"

_RULES_JVM_EXTERNAL_SHA = "d31e369b854322ca5098ea12c69d7175ded971435e55c18dd9dd5f29cc5249ac"

# Setup Kotlin

http_archive(
    name = "rules_kotlin",
    sha256 = "3b772976fec7bdcda1d84b9d39b176589424c047eb2175bed09aac630e50af43",
    url = "https://github.com/bazelbuild/rules_kotlin/releases/download/v1.9.6/rules_kotlin-v1.9.6.tar.gz",
)

load("@rules_kotlin//kotlin:repositories.bzl", "kotlin_repositories", "kotlinc_version", "versions")

kotlin_repositories(
    compiler_release = kotlinc_version(
        release = _KOTLIN_COMPILER_VERSION,
        sha256 = _KOTLIN_COMPILER_SHA,
    ),
)

register_toolchains("//:kotlin_toolchain")

## JVM External

http_archive(
    name = "rules_jvm_external",
    sha256 = _RULES_JVM_EXTERNAL_SHA,
    strip_prefix = "rules_jvm_external-%s" % _RULES_JVM_EXTERNAL_TAG,
    url = "https://github.com/bazelbuild/rules_jvm_external/releases/download/%s/rules_jvm_external-%s.tar.gz" % (
        _RULES_JVM_EXTERNAL_TAG,
        _RULES_JVM_EXTERNAL_TAG,
    ),
)

load("@rules_jvm_external//:defs.bzl", "maven_install")

maven_install(
    artifacts = [
        "androidx.compose.compiler:compiler:{}".format(_COMPOSE_COMPILER_VERSION),
        "org.jetbrains.kotlin:kotlin-stdlib:{}".format(_KOTLIN_COMPILER_VERSION),
        "androidx.core:core-ktx:1.7.0",
        "androidx.appcompat:appcompat:1.4.1",
        "androidx.activity:activity-compose:1.4.0",
        "androidx.compose.material:material:{}".format(_COMPOSE_VERSION),
        "androidx.compose.ui:ui:{}".format(_COMPOSE_VERSION),
        "androidx.compose.ui:ui-tooling:{}".format(_COMPOSE_VERSION),
        "androidx.compose.runtime:runtime:{}".format(_COMPOSE_VERSION),
    ],
    repositories = [
        "https://maven.google.com",
        "https://repo1.maven.org/maven2",
    ],
)

http_archive(
    name = "bazel_skylib",
    sha256 = _SKYLIB_SHA,
    urls = ["https://github.com/bazelbuild/bazel-skylib/releases/download/%s/bazel-skylib-%s.tar.gz" % (
        _SKYLIB_VERSION,
        _SKYLIB_VERSION,
    )],
)

## Android

http_archive(
    name = "rules_android",
    sha256 = _ANDROID_SHA,
    strip_prefix = "rules_android-%s" % _ANDROID_VERSION,
    urls = ["https://github.com/bazelbuild/rules_android/archive/v%s.zip" % _ANDROID_VERSION],
)

#load("@rules_android//android:rules.bzl", "android_sdk_repository")

android_sdk_repository(name = "androidsdk")

#android_ndk_repository(name = "androidndk")
