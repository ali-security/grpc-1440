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

load("//bazel:grpc_build_system.bzl", "grpc_cc_test", "grpc_package")

licenses(["notice"])

grpc_package(name = "test/core/surface")

grpc_cc_test(
    name = "grpc_byte_buffer_reader_test",
    srcs = ["byte_buffer_reader_test.cc"],
    language = "C++",
    uses_polling = False,
    deps = [
        "//:gpr",
        "//:grpc",
        "//test/core/util:grpc_test_util",
    ],
)

grpc_cc_test(
    name = "channel_create_test",
    srcs = ["channel_create_test.cc"],
    language = "C++",
    deps = [
        "//:gpr",
        "//:grpc",
        "//test/core/util:grpc_test_util",
    ],
)

grpc_cc_test(
    name = "grpc_completion_queue_test",
    srcs = ["completion_queue_test.cc"],
    language = "C++",
    deps = [
        "//:gpr",
        "//:grpc",
        "//test/core/util:grpc_test_util",
    ],
)

grpc_cc_test(
    name = "completion_queue_threading_test",
    srcs = ["completion_queue_threading_test.cc"],
    flaky = True,  # TODO(b/153064668)
    language = "C++",
    deps = [
        "//:gpr",
        "//:grpc",
        "//test/core/util:grpc_test_util",
    ],
)

grpc_cc_test(
    name = "concurrent_connectivity_test",
    srcs = ["concurrent_connectivity_test.cc"],
    language = "C++",
    deps = [
        "//:gpr",
        "//:grpc",
        "//test/core/util:grpc_test_util",
    ],
)

grpc_cc_test(
    name = "init_test",
    srcs = ["init_test.cc"],
    external_deps = [
        "gtest",
    ],
    language = "C++",
    uses_polling = False,
    deps = [
        "//:gpr",
        "//:grpc",
        "//test/core/util:grpc_test_util",
    ],
)

grpc_cc_test(
    name = "lame_client_test",
    srcs = ["lame_client_test.cc"],
    language = "C++",
    deps = [
        "//:gpr",
        "//:grpc",
        "//test/core/end2end:cq_verifier",
        "//test/core/util:grpc_test_util",
    ],
)

grpc_cc_test(
    name = "num_external_connectivity_watchers_test",
    srcs = ["num_external_connectivity_watchers_test.cc"],
    data = [
        "//src/core/tsi/test_creds:ca.pem",
    ],
    language = "C++",
    deps = [
        "//:gpr",
        "//:grpc",
        "//test/core/util:grpc_test_util",
    ],
)

grpc_cc_test(
    name = "public_headers_must_be_c89",
    srcs = ["public_headers_must_be_c89.c"],
    language = "C",
    deps = [
        "//:gpr",
        "//:grpc",
        "//:grpc_authorization_provider",
        "//test/core/util:grpc_test_util",
    ],
)

grpc_cc_test(
    name = "secure_channel_create_test",
    srcs = ["secure_channel_create_test.cc"],
    language = "C++",
    deps = [
        "//:gpr",
        "//:grpc",
        "//test/core/util:grpc_test_util",
    ],
)

grpc_cc_test(
    name = "sequential_connectivity_test",
    srcs = ["sequential_connectivity_test.cc"],
    data = [
        "//src/core/tsi/test_creds:ca.pem",
        "//src/core/tsi/test_creds:server1.key",
        "//src/core/tsi/test_creds:server1.pem",
    ],
    flaky = True,  # TODO(b/151696318)
    language = "C++",
    deps = [
        "//:gpr",
        "//:grpc",
        "//test/core/util:grpc_test_util",
    ],
)

grpc_cc_test(
    name = "server_chttp2_test",
    srcs = ["server_chttp2_test.cc"],
    external_deps = [
        "gtest",
    ],
    language = "C++",
    deps = [
        "//:gpr",
        "//:grpc",
        "//test/core/util:grpc_test_util",
    ],
)

grpc_cc_test(
    name = "server_test",
    srcs = ["server_test.cc"],
    language = "C++",
    deps = [
        "//:gpr",
        "//:grpc",
        "//test/core/util:grpc_test_util",
    ],
)
