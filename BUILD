load("@bazel_tools//tools/jdk:default_java_toolchain.bzl", "default_java_toolchain")
load("@rules_kotlin//kotlin:core.bzl", "define_kt_toolchain", "kt_compiler_plugin")

# Java Toolchain

default_java_toolchain(
    name = "java_toolchain",
    visibility = ["//visibility:public"],
)

define_kt_toolchain(
    name = "kotlin_toolchain",
    jvm_target = "1.8",
)

# Define the compose compiler plugin
# Used by referencing //:jetpack_compose_compiler_plugin

kt_compiler_plugin(
    name = "jetpack_compose_compiler_plugin",
    id = "androidx.compose.compiler",
    target_embedded_compiler = True,
    visibility = ["//visibility:public"],
    deps = [
        "@maven//:androidx_compose_compiler_compiler",
    ],
)

platform(
    name = "arm64-v8a",
    constraint_values = [
        "@platforms//cpu:arm64",
        "@platforms//os:android",
    ],
)
