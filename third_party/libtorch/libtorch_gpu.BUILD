load("@rules_cc//cc:defs.bzl", "cc_library")
load("@local_config_cuda//cuda:build_defs.bzl", "if_cuda")
package(default_visibility = ["//visibility:public"])

licenses(["notice"])

cc_library(
  name = "libtorch_gpu",
   deps = [
        "@local_config_python//:python_headers",
        "@local_config_python//:python_lib",
   ] + if_cuda(["libtorch_nvidia"])
)

cc_library(
    name = "libtorch_nvidia",
    includes = [
        "nvidia/include",
        "nvidia/include/torch/csrc/api/include",
    ],
    linkopts = [
        "-L/usr/local/libtorch_gpu/nvidia/lib",
        "-lc10",
        "-lc10_cuda", 
        "-ltorch",
        "-ltorch_cpu",
        "-ltorch_cuda",
    ],
    linkstatic = False,
    deps = [
        "@local_config_cuda//cuda:cudart",
    ],
)

