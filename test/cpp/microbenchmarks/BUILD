# Copyright 2017 gRPC authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

load("//bazel:grpc_build_system.bzl", "grpc_cc_library", "grpc_cc_test", "grpc_package")
load("//test/cpp/microbenchmarks:grpc_benchmark_config.bzl", "grpc_benchmark_args")

licenses(["notice"])

grpc_package(name = "test/cpp/microbenchmarks")

grpc_cc_test(
    name = "noop-benchmark",
    srcs = ["noop-benchmark.cc"],
    external_deps = [
        "benchmark",
    ],
    deps = ["//test/core/util:grpc_test_util"],
)

grpc_cc_library(
    name = "helpers",
    testonly = 1,
    srcs = ["helpers.cc"],
    hdrs = [
        "fullstack_context_mutators.h",
        "fullstack_fixtures.h",
        "helpers.h",
    ],
    external_deps = [
        "benchmark",
    ],
    deps = [
        "//:grpc++_unsecure",
        "//src/proto/grpc/testing:echo_proto",
        "//test/core/util:grpc_test_util_unsecure",
        "//test/cpp/util:test_config",
    ],
)

# Need a secure version of helpers to benchmark opencensus
grpc_cc_library(
    name = "helpers_secure",
    testonly = 1,
    srcs = ["helpers.cc"],
    hdrs = [
        "fullstack_context_mutators.h",
        "fullstack_fixtures.h",
        "helpers.h",
    ],
    external_deps = [
        "benchmark",
    ],
    deps = [
        "//:grpc++",
        "//src/proto/grpc/testing:echo_proto",
        "//test/core/util:grpc_test_util",
        "//test/cpp/util:test_config",
    ],
)

grpc_cc_test(
    name = "bm_closure",
    srcs = ["bm_closure.cc"],
    args = grpc_benchmark_args(),
    tags = [
        "no_mac",
        "no_windows",
    ],
    deps = [":helpers"],
)

grpc_cc_test(
    name = "bm_alarm",
    srcs = ["bm_alarm.cc"],
    args = grpc_benchmark_args(),
    tags = [
        "no_mac",
        "no_windows",
    ],
    deps = [":helpers"],
)

grpc_cc_test(
    name = "bm_arena",
    size = "large",
    srcs = ["bm_arena.cc"],
    args = grpc_benchmark_args(),
    tags = [
        "no_mac",
        "no_windows",
        "notsan",
    ],
    uses_polling = False,
    deps = [":helpers"],
)

grpc_cc_test(
    name = "bm_byte_buffer",
    srcs = ["bm_byte_buffer.cc"],
    args = grpc_benchmark_args(),
    tags = [
        "no_mac",
        "no_windows",
    ],
    uses_polling = False,
    deps = [":helpers"],
)

grpc_cc_test(
    name = "bm_channel",
    srcs = ["bm_channel.cc"],
    args = grpc_benchmark_args(),
    tags = [
        "no_mac",
        "no_windows",
    ],
    uses_polling = False,
    deps = [":helpers"],
)

grpc_cc_test(
    name = "bm_call_create",
    srcs = ["bm_call_create.cc"],
    args = grpc_benchmark_args(),
    tags = [
        "no_mac",
        "no_windows",
    ],
    uses_polling = False,
    deps = [":helpers"],
)

grpc_cc_test(
    name = "bm_cq",
    srcs = ["bm_cq.cc"],
    args = grpc_benchmark_args(),
    tags = [
        "no_mac",
        "no_windows",
    ],
    deps = [":helpers"],
)

grpc_cc_test(
    name = "bm_cq_multiple_threads",
    srcs = ["bm_cq_multiple_threads.cc"],
    args = grpc_benchmark_args(),
    tags = [
        "no_mac",
        "no_windows",
    ],
    uses_polling = False,
    deps = [":helpers"],
)

grpc_cc_test(
    name = "bm_error",
    srcs = ["bm_error.cc"],
    args = grpc_benchmark_args(),
    tags = [
        "no_mac",
        "no_windows",
    ],
    uses_polling = False,
    deps = [":helpers"],
)

grpc_cc_library(
    name = "fullstack_streaming_ping_pong_h",
    testonly = 1,
    hdrs = [
        "fullstack_streaming_ping_pong.h",
    ],
    tags = [
        "no_mac",
        "no_windows",
    ],
    deps = [":helpers"],
)

grpc_cc_test(
    name = "bm_fullstack_streaming_ping_pong",
    size = "large",
    srcs = [
        "bm_fullstack_streaming_ping_pong.cc",
    ],
    args = grpc_benchmark_args(),
    tags = [
        "no_mac",  # to emulate "excluded_poll_engines: poll"
        "no_windows",
    ],
    deps = [":fullstack_streaming_ping_pong_h"],
)

grpc_cc_library(
    name = "fullstack_streaming_pump_h",
    testonly = 1,
    hdrs = [
        "fullstack_streaming_pump.h",
    ],
    deps = [":helpers"],
)

grpc_cc_test(
    name = "bm_fullstack_streaming_pump",
    srcs = [
        "bm_fullstack_streaming_pump.cc",
    ],
    args = grpc_benchmark_args(),
    tags = [
        "no_mac",  # to emulate "excluded_poll_engines: poll"
        "no_windows",
    ],
    deps = [":fullstack_streaming_pump_h"],
)

grpc_cc_library(
    name = "fullstack_unary_ping_pong_h",
    testonly = 1,
    hdrs = [
        "fullstack_unary_ping_pong.h",
    ],
    deps = [":helpers"],
)

grpc_cc_test(
    name = "bm_fullstack_unary_ping_pong",
    size = "large",
    srcs = [
        "bm_fullstack_unary_ping_pong.cc",
    ],
    args = grpc_benchmark_args(),
    tags = [
        "no_mac",  # to emulate "excluded_poll_engines: poll"
        "no_windows",
    ],
    deps = [":fullstack_unary_ping_pong_h"],
)

grpc_cc_test(
    name = "bm_chttp2_hpack",
    srcs = ["bm_chttp2_hpack.cc"],
    args = grpc_benchmark_args(),
    tags = [
        "no_mac",
        "no_windows",
    ],
    uses_polling = False,
    deps = [":helpers"],
)

grpc_cc_test(
    name = "bm_chttp2_transport",
    srcs = ["bm_chttp2_transport.cc"],
    args = grpc_benchmark_args(),
    tags = [
        "no_mac",
        "no_windows",
        "nomsan",
    ],
    deps = [":helpers"],
)

grpc_cc_test(
    name = "bm_opencensus_plugin",
    srcs = ["bm_opencensus_plugin.cc"],
    args = grpc_benchmark_args(),
    language = "C++",
    deps = [
        ":helpers_secure",
        "//:grpc_opencensus_plugin",
        "//src/proto/grpc/testing:echo_proto",
    ],
)

grpc_cc_test(
    name = "bm_timer",
    srcs = ["bm_timer.cc"],
    args = grpc_benchmark_args(),
    tags = [
        "no_mac",
        "no_windows",
    ],
    uses_polling = False,
    deps = [":helpers"],
)

grpc_cc_test(
    name = "bm_pollset",
    srcs = ["bm_pollset.cc"],
    args = grpc_benchmark_args(),
    tags = [
        "no_mac",
        "no_windows",
    ],
    deps = [":helpers"],
)

grpc_cc_test(
    name = "bm_threadpool",
    size = "large",
    srcs = ["bm_threadpool.cc"],
    args = grpc_benchmark_args(),
    tags = [
        "manual",
        "no_windows",
        "notap",
    ],
    uses_polling = False,
    deps = [":helpers"],
)

grpc_cc_library(
    name = "bm_callback_test_service_impl",
    testonly = 1,
    srcs = ["callback_test_service.cc"],
    hdrs = ["callback_test_service.h"],
    external_deps = [
        "benchmark",
    ],
    deps = [
        ":helpers",
        "//src/proto/grpc/testing:echo_proto",
        "//test/cpp/util:test_util_unsecure",
    ],
)

grpc_cc_library(
    name = "callback_unary_ping_pong_h",
    testonly = 1,
    hdrs = [
        "callback_unary_ping_pong.h",
    ],
    deps = [
        ":bm_callback_test_service_impl",
        ":helpers",
    ],
)

grpc_cc_test(
    name = "bm_callback_unary_ping_pong",
    size = "large",
    srcs = [
        "bm_callback_unary_ping_pong.cc",
    ],
    args = grpc_benchmark_args(),
    tags = [
        "manual",
        "no_mac",
        "no_windows",
        "notap",
    ],
    deps = [":callback_unary_ping_pong_h"],
)

grpc_cc_library(
    name = "callback_streaming_ping_pong_h",
    testonly = 1,
    hdrs = [
        "callback_streaming_ping_pong.h",
    ],
    deps = [
        ":bm_callback_test_service_impl",
        ":helpers",
    ],
)

grpc_cc_test(
    name = "bm_callback_streaming_ping_pong",
    size = "large",
    srcs = [
        "bm_callback_streaming_ping_pong.cc",
    ],
    args = grpc_benchmark_args(),
    tags = [
        "manual",
        "no_mac",
        "no_windows",
        "notap",
    ],
    deps = [":callback_streaming_ping_pong_h"],
)
