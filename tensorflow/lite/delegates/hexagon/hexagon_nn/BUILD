# Copyright 2019 The TensorFlow Authors. All Rights Reserved.
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
# ==============================================================================

package(default_visibility = [
    "//visibility:public",
])

licenses(["notice"])  # Apache 2.0

cc_library(
    name = "hexagon_nn_header",
    hdrs = [
        "hexagon_nn.h",
        "hexagon_nn_init.h",
    ],
    deps = [
        "@hexagon_nn//:hexagon_nn_header",
    ],
)

genrule(
    name = "libhexagon_interface",
    srcs = [] + select({
        "//tensorflow:android_arm64": ["@hexagon_nn//:hexagon/arm64-v8a/libhexagon_interface.so"],
        "//tensorflow:android_arm": ["@hexagon_nn//:hexagon/armeabi-v7a/libhexagon_interface.so"],
        "//conditions:default": [],
    }),
    outs = ["libhexagon_interface.so"],
    cmd = "cp $(SRCS) $(@D)",
    local = 1,
    output_to_bindir = 1,
)
