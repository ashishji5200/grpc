workspace(name = "com_github_grpc_grpc")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("//bazel:grpc_deps.bzl", "grpc_deps", "grpc_test_only_deps")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

grpc_deps()

grpc_test_only_deps()

register_execution_platforms(
    "//third_party/toolchains:rbe_ubuntu1604",
    "//third_party/toolchains:rbe_ubuntu1604_large",
)

register_toolchains(
    "//third_party/toolchains:cc-toolchain-clang-x86_64-default",
)

# TODO(https://github.com/grpc/grpc/issues/18331): Move off of this dependency.
git_repository(
    name = "org_pubref_rules_protobuf",
    remote = "https://github.com/ghostwriternr/rules_protobuf",
    tag = "v0.8.2.1-alpha",
)

git_repository(
    name = "io_bazel_rules_python",
    commit = "8b5d0683a7d878b28fffe464779c8a53659fc645",
    remote = "https://github.com/bazelbuild/rules_python.git",
)

load("@io_bazel_rules_python//python:pip.bzl", "pip_repositories", "pip_import")

pip_import(
    name = "grpc_python_dependencies",
    requirements = "//:requirements.bazel.txt",
)

http_archive(
    name = "cython",
    build_file = "//third_party:cython.BUILD",
    sha256 = "d68138a2381afbdd0876c3cb2a22389043fa01c4badede1228ee073032b07a27",
    strip_prefix = "cython-c2b80d87658a8525ce091cbe146cb7eaa29fed5c",
    urls = [
        "https://github.com/cython/cython/archive/c2b80d87658a8525ce091cbe146cb7eaa29fed5c.tar.gz",
    ],
)

load("//bazel:grpc_python_deps.bzl", "grpc_python_deps")

grpc_python_deps()
