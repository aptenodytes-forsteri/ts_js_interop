load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive", "http_file")

http_archive(
        name = "aspect_rules_js",
        sha256 = "4cab6898f0ff8048e32640cce06a47aa4b92b2fb330d055940f95f24c8ebb868",
        strip_prefix = "rules_js-2.0.1",
        url = "https://artifactory.internal.bosdyn.com/artifactory/github-remote/aspect-build/rules_js/releases/download/v2.0.1/rules_js-v2.0.1.tar.gz",
    )

http_archive(
    name = "aspect_rules_ts",
    sha256 = "5aafa2422b6f2ed6d8db9edcd6368693055960bca7e149516b95c0d45a6a7ae5",
    strip_prefix = "rules_ts-3.1.0",
    url = "https://artifactory.internal.bosdyn.com/artifactory/github-remote/aspect-build/rules_ts/releases/download/v3.1.0/rules_ts-v3.1.0.tar.gz",
)

http_archive(
    name = "aspect_rules_swc",
    sha256 = "d63d7b283249fa942f78d2716ecff3edbdc10104ee1b9a6b9464ece471ef95ea",
    strip_prefix = "rules_swc-2.0.0",
    url = "https://artifactory.internal.bosdyn.com/artifactory/github-remote/aspect-build/rules_swc/releases/download/v2.0.0/rules_swc-v2.0.0.tar.gz",
)


load("@aspect_rules_js//js:repositories.bzl", "rules_js_dependencies")
load("@aspect_rules_ts//ts:repositories.bzl", "rules_ts_dependencies")
load("@aspect_rules_swc//swc:dependencies.bzl", "rules_swc_dependencies")

rules_js_dependencies()
rules_ts_dependencies(
  # Retrieve TypeScript version from package.json.
  ts_version_from = "//:package.json",
)
rules_swc_dependencies()

load("@aspect_rules_js//js:toolchains.bzl", "DEFAULT_NODE_VERSION", "rules_js_register_toolchains")

rules_js_register_toolchains(node_version = DEFAULT_NODE_VERSION)

# Register aspect_bazel_lib toolchains;
# If you use npm_translate_lock or npm_import from aspect_rules_js you can omit this block.
load("@aspect_bazel_lib//lib:repositories.bzl", "register_copy_directory_toolchains", "register_copy_to_directory_toolchains", "register_coreutils_toolchains")

register_copy_directory_toolchains()

register_copy_to_directory_toolchains()

register_coreutils_toolchains()

load("@aspect_rules_swc//swc:repositories.bzl", "LATEST_SWC_VERSION", "swc_register_toolchains")

swc_register_toolchains(
    name = "swc",
    swc_version = LATEST_SWC_VERSION,
)



