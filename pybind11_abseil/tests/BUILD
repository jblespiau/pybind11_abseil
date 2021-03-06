# Tests and examples for pybind11_abseil.

# load("//devtools/python/blaze:python3.bzl", "py2and3_strict_test")
load("@pybind11_bazel//:build_defs.bzl", "pybind_extension")

licenses(["notice"])

pybind_extension(
    name = "absl_example",
    srcs = ["absl_example.cc"],
    deps = [
        "//pybind11_abseil:absl_casters",
        "//pybind11_abseil:absl_numpy_span_caster",
        "@com_google_absl//absl/container:flat_hash_set",
        "@com_google_absl//absl/strings",
        "@com_google_absl//absl/time",
        "@com_google_absl//absl/types:optional",
        "@com_google_absl//absl/types:span",
    ],
)

py_test(
    name = "absl_test",
    srcs = ["absl_test.py"],
    data = [":absl_example.so"],
    srcs_version = "PY2AND3",
)

pybind_extension(
    name = "missing_import",
    srcs = ["missing_import.cc"],
    copts = ["-UNDEBUG"],
    deps = [
        "//pybind11_abseil:status_casters",
        "@com_google_absl//absl/status",
        "@com_google_absl//absl/status:statusor",
    ],
)

py_test(
    name = "missing_import_test",
    srcs = ["missing_import_test.py"],
    data = [":missing_import.so"],
    srcs_version = "PY2AND3",
)

pybind_extension(
    name = "status_example",
    srcs = ["status_example.cc"],
    deps = [
        "//pybind11_abseil:status_casters",
        "@com_google_absl//absl/status",
        "@com_google_absl//absl/status:statusor",
    ],
)

py_test(
    name = "status_test",
    srcs = ["status_test.py"],
    data = [
        ":status_example.so",
        "//pybind11_abseil:status.so",
    ],
    srcs_version = "PY2AND3",
)
