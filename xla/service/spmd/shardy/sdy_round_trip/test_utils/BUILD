load("//xla/tsl/platform:rules_cc.bzl", "cc_library")

package(
    # copybara:uncomment default_applicable_licenses = ["//tensorflow:license"],
    default_visibility = [":friends"],
    licenses = ["notice"],
)

package_group(
    name = "friends",
    packages = [
        "//learning/deepmind/partir/compiler/shardonnay/...",
        "//third_party/openxla/shardy/tools/...",
        "//xla/service/spmd/shardy/...",
    ],
)

cc_library(
    name = "mhlo_to_hlo_to_mhlo",
    srcs = ["mhlo_to_hlo_to_mhlo.cc"],
    hdrs = ["mhlo_to_hlo_to_mhlo.h"],
    deps = [
        "//xla/hlo/ir:hlo",
        "//xla/hlo/translate:stablehlo",
        "//xla/hlo/translate/hlo_to_mhlo:hlo_to_mlir_hlo",
        "//xla/mlir_hlo:mhlo_passes",
        "//xla/service:hlo_module_config",
        "//xla/service:hlo_proto_cc",
        "@com_google_absl//absl/log",
        "@com_google_absl//absl/status",
        "@com_google_absl//absl/status:statusor",
        "@com_google_absl//absl/strings",
        "@llvm-project//llvm:Support",
        "@llvm-project//mlir:IR",
        "@llvm-project//mlir:Pass",
        "@llvm-project//mlir:Support",
        "@tsl//tsl/platform:statusor",
    ],
)

cc_library(
    name = "testing_pipeline",
    srcs = ["testing_pipeline.cc"],
    hdrs = ["testing_pipeline.h"],
    deps = [
        ":mhlo_to_hlo_to_mhlo",
        "//xla/service/spmd/shardy/sdy_round_trip:pipelines",
        "@llvm-project//mlir:Pass",
    ],
)
