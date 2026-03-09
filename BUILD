load("@npm//:defs.bzl", "npm_link_all_packages")
npm_link_all_packages(name = "node_modules")

load("@npm//:protobufjs-cli/package_json.bzl", "bin")

bin.pbjs(
  name = "gen",
  srcs = ["data.proto"],
  outs = ["data.js"],
  args = [
      "-t", "static-module",
      "-w", "commonjs",
      "-o", "data.js",
      "data.proto",
  ],
)
