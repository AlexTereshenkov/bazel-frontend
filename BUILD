load("@npm//:defs.bzl", "npm_link_all_packages")
npm_link_all_packages(name = "node_modules")

load("@npm//:protobufjs/package_json.bzl", "bin")

PROTOBUF_DEPS = [
    "//:node_modules/protobufjs",
    # these deps are needed even though they are not automatic transitive deps of
    # protobufjs since if they are not in the runfiles then protobufjs attempts to
    # run `npm install` at runtime to get thhem which fails as it tries to access
    # the npm cache outside of the sandbox
    "//:node_modules/semver",
    "//:node_modules/chalk",
    #"//:node_modules/glob",
    #"//:node_modules/jsdoc",
    "//:node_modules/minimist",
    #"//:node_modules/tmp",
    "//:node_modules/uglify-js",
    #"//:node_modules/uglify-es",
    #"//:node_modules/espree",
    "//:node_modules/escodegen",
    #"//:node_modules/estraverse",
]

bin.pbjs(
  name = "gen",
  srcs = ["data.proto"] + PROTOBUF_DEPS,
  outs = ["data.js"],
  args = [
      "-t", "static-module",
      "-w", "commonjs",
      "-o", "data.js",
      "data.proto",
  ],
)
