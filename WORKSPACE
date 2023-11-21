


load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

BZLMODRIO_COMMITISH = "77dae7eabf1517ea58cf90d854f7d9d5a81561e6"
BZLMODRIO_SHA256 = "9e62b75600a972cee1bafdb6fc8d43be0690db496c421cebf2c9376d92f564e5"
http_archive(
    name = "bzlmodrio",
    url = "https://github.com/bzlmodRio/bzlmodRio/archive/{}.tar.gz".format(BZLMODRIO_COMMITISH),
    sha256 = BZLMODRIO_SHA256,
    strip_prefix = "bzlmodRio-{}".format(BZLMODRIO_COMMITISH),
)


load("@bzlmodrio//private/non_bzlmod:download_dependencies.bzl", "download_dependencies")
download_dependencies(
        allwpilib_version = "2024.1.1-beta-3",
        apriltaglib_version = None,
        imgui_version = None,
        libssh_version = None,
        navx_version = None,
        phoenix_version = None,
        revlib_version = None,
        rules_pmd_version = None,
        rules_wpi_styleguide_version = None,
        photonlib_version = None,
        pathplannerlib_version = None,

        # Always the default version of these libraries
        # rules_spotless_version = None,
        # rules_wpi_styleguide_version = None,
        # ni_version = None,
        # opencv_version = None,
        # rules_bazelrio_version = None,
        # rules_toolchains_version = None,
        # rules_checkstyle_version = None,
    )

load("@bzlmodrio//private/non_bzlmod:setup_dependencies.bzl", "get_java_dependencies", "setup_dependencies")

load("@rules_jvm_external//:defs.bzl", "maven_install")

setup_dependencies()

maven_artifacts, maven_repositories = get_java_dependencies()
maven_install(
        name = "maven",
        artifacts = maven_artifacts + [
            # "com.google.guava:guava:21.0",
            # "org.fxmisc.easybind:easybind:1.0.3",
            "org.junit.jupiter:junit-jupiter-api:5.8.2",
            "org.junit.jupiter:junit-jupiter-params:5.8.2",
            "org.junit.jupiter:junit-jupiter-engine:5.8.2",
            "org.junit.platform:junit-platform-commons:1.6.1",
            "org.junit.platform:junit-platform-console:1.6.1",
            "org.junit.platform:junit-platform-engine:1.6.1",
            "org.junit.platform:junit-platform-launcher:1.6.1",
            "org.junit.platform:junit-platform-suite-api:1.6.1",
            # "org.snobotv2:snobot_sim_java:{v}".format(v = SNOBOTSIM_VERSION),
            # "org.snobotv2:snobot_swerve_sim:{v}".format(v = SNOBOTSIM_VERSION),
        ],
        repositories = maven_repositories + ["https://raw.githubusercontent.com/snobotsim/maven_repo/master/release", "https://raw.githubusercontent.com/snobotsim/maven_repo/master/development"],
        # maven_install_json = "//build_scripts/bazel/deps:maven_install.json",
    )


http_archive(
    name = "rules_proto",
    sha256 = "dc3fb206a2cb3441b485eb1e423165b231235a1ea9b031b4433cf7bc1fa460dd",
    strip_prefix = "rules_proto-5.3.0-21.7",
    urls = [
        "https://github.com/bazelbuild/rules_proto/archive/refs/tags/5.3.0-21.7.tar.gz",
    ],
)

load("@rules_proto//proto:repositories.bzl", "rules_proto_dependencies", "rules_proto_toolchains")

rules_proto_dependencies()

rules_proto_toolchains()


load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_file")

QUICKBUF_VERSION = "1.3.2"

http_file(
    name = "quickbuffer_protoc_linux",
    url = "https://repo1.maven.org/maven2/us/hebi/quickbuf/protoc-gen-quickbuf/" + QUICKBUF_VERSION + "/protoc-gen-quickbuf-" + QUICKBUF_VERSION + "-linux-x86_64.exe",
    sha256 = "f9a041bccaa7040db523666ef1b5fe9f6f94e70a82c88951f18f58aadd9c50b5",
    executable = True,
)
http_file(
    name = "quickbuffer_protoc_osx",
    url = "https://repo1.maven.org/maven2/us/hebi/quickbuf/protoc-gen-quickbuf/" + QUICKBUF_VERSION + "/protoc-gen-quickbuf-" + QUICKBUF_VERSION + "-osx-x86_64.exe   ",
    sha256 = "ea307c2b69664ae7e7c69db4cddf5803187e5a34bceffd09a21652f0f16044f7",
    executable = True,
)
http_file(
    name = "quickbuffer_protoc_windows",
    url = "https://repo1.maven.org/maven2/us/hebi/quickbuf/protoc-gen-quickbuf/" + QUICKBUF_VERSION + "/protoc-gen-quickbuf-" + QUICKBUF_VERSION + "-windows-x86_64.exe ",
    sha256 = "27dc1f29764a62b5e6a813a4bcd63e81bbdc3394da760a44acae1025b4a89f1d",
    executable = True,
)

http_archive(
        name = "gtest",
        sha256 = "8ad598c73ad796e0d8280b082cebd82a630d73e73cd3c70057938a6501bba5d7",
        strip_prefix = "googletest-1.14.0",
        urls = ["https://github.com/google/googletest/archive/refs/tags/v1.14.0.tar.gz"],
    )