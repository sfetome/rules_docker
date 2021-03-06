# Copyright 2017 The Bazel Authors. All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
package(default_visibility = ["//visibility:public"])

licenses(["notice"])  # Apache 2.0

exports_files(["push-all.sh.tpl"])

exports_files(["structure-test.sh.tpl"])

exports_files(["compare_ids_test.py"])

exports_files(["compare_ids_test.bzl"])

exports_files(["extract_image_id.py"])

py_binary(
    name = "extract_image_id",
    srcs = [":extract_image_id.py"],
    deps = [":extract_image_id_lib"],
    legacy_create_init = False,
)

py_library(
    name = "extract_image_id_lib",
    srcs = [":extract_image_id.py"],
)

py_binary(
    name = "compare_ids_test",
    srcs = [":compare_ids_test.py"],
    deps = [":extract_image_id_lib"],
    legacy_create_init = False
)

alias(
    name = "structure_test_executable",
    actual = select({
        "//conditions:default": "@structure_test_linux//file",
        "@bazel_tools//src/conditions:darwin": "@structure_test_darwin//file",
        "@bazel_tools//src/conditions:darwin_x86_64": "@structure_test_darwin//file",
    }),
)

py_binary(
    name = "idd",
    srcs = ["idd.py"],
    legacy_create_init = False
)
