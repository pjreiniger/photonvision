load("@rules_proto//proto:defs.bzl", "proto_lang_toolchain")

alias(
    name = "quickbuf_protoc",
    actual = select({
        "@bazel_tools//src/conditions:darwin": "@quickbuffer_protoc_osx//file",
        "@bazel_tools//src/conditions:windows": "@quickbuffer_protoc_windows//file",
        "@rules_bzlmodrio_toolchains//constraints/combined:is_linux": "@quickbuffer_protoc_linux//file",
    }),
    visibility = ["//visibility:public"],
)

proto_lang_toolchain(
    name = "quickbuf_toolchain",
    command_line = "--quickbuf_out=gen_descriptors=true:$(OUT)",
    plugin = ":quickbuf_protoc",
    plugin_format_flag = "--plugin=protoc-gen-quickbuf=%s",
    runtime = "@maven//:us_hebi_quickbuf_quickbuf_runtime",
    visibility = ["//visibility:public"],
)