# gazelle:ignore
package(default_visibility = ["//visibility:public"])

load("@io_bazel_rules_go//go:def.bzl", "go_test")
load("//mixer/tools/codegen:generate.bzl", "mixer_supported_template_library")

mixer_supported_template_library(
    name = "go_default_library",
    packages = {
        "//mixer/template/sample/report:go_default_library_proto.descriptor_set": "istio.io/istio/mixer/template/sample/report",
        "//mixer/template/sample/check:go_default_library_proto.descriptor_set": "istio.io/istio/mixer/template/sample/check",
        "//mixer/template/sample/quota:go_default_library_proto.descriptor_set": "istio.io/istio/mixer/template/sample/quota",
    },
    deps = [
        "//mixer/template/sample/check:go_default_library",
        "//mixer/template/sample/quota:go_default_library",
        "//mixer/template/sample/report:go_default_library",
    ],
)

go_test(
    name = "go_default_test",
    size = "small",
    srcs = ["template.gen_test.go"],
    library = ":go_default_library",
    deps = [
        "//mixer/pkg/adapter:go_default_library",
        "//mixer/pkg/attribute:go_default_library",
        "//mixer/pkg/config/descriptor:go_default_library",
        "//mixer/pkg/config/proto:go_default_library",
        "//mixer/pkg/expr:go_default_library",
        "//mixer/pkg/il/evaluator:go_default_library",
        "//mixer/template/sample/check:go_default_library",
        "//mixer/template/sample/quota:go_default_library",
        "//mixer/template/sample/report:go_default_library",
        "@com_github_davecgh_go_spew//spew:go_default_library",
        "@com_github_ghodss_yaml//:go_default_library",
        "@com_github_gogo_protobuf//proto:go_default_library",
        "@com_github_golang_protobuf//ptypes/empty:go_default_library",
        "@com_github_googleapis_googleapis//:google/rpc",
        "@io_istio_api//:mixer/v1/config/descriptor",
        "@io_istio_api//:mixer/v1/template",
    ],
)
