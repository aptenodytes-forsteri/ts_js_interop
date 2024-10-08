load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive", "http_file")

http_archive(
        name = "aspect_rules_js",
        sha256 = "4cab6898f0ff8048e32640cce06a47aa4b92b2fb330d055940f95f24c8ebb868",
        strip_prefix = "rules_js-2.0.1",
        url = "https://github.com/aspect-build/rules_js/releases/download/v2.0.1/rules_js-v2.0.1.tar.gz",
    )

http_archive(
    name = "aspect_rules_ts",
    sha256 = "d23ba2b800493a83c3ec9e300e01c74a7b0a58c08893e681417e2c2f48f8c4bb",
    strip_prefix = "rules_ts-3.2.0",
    url = "https://github.com/aspect-build/rules_ts/releases/download/v3.2.0/rules_ts-v3.2.0.tar.gz",
)

http_archive(
    name = "aspect_rules_swc",
    sha256 = "d63d7b283249fa942f78d2716ecff3edbdc10104ee1b9a6b9464ece471ef95ea",
    strip_prefix = "rules_swc-2.0.0",
    url = "https://github.com/aspect-build/rules_swc/releases/download/v2.0.0/rules_swc-v2.0.0.tar.gz",
)

http_archive(
    name = "aspect_rules_esbuild",
    sha256 = "550e33ddeb86a564b22b2c5d3f84748c6639b1b2b71fae66bf362c33392cbed8",
    strip_prefix = "rules_esbuild-0.21.0",
    url = "https://github.com/aspect-build/rules_esbuild/releases/download/v0.21.0/rules_esbuild-v0.21.0.tar.gz",
)


load("@aspect_rules_js//js:repositories.bzl", "rules_js_dependencies")
load("@aspect_rules_ts//ts:repositories.bzl", "rules_ts_dependencies")
load("@aspect_rules_swc//swc:dependencies.bzl", "rules_swc_dependencies")
load("@aspect_rules_esbuild//esbuild:dependencies.bzl", "rules_esbuild_dependencies")

rules_js_dependencies()
rules_ts_dependencies(
  # Retrieve TypeScript version from package.json.
  ts_version_from = "//:package.json",
)
rules_swc_dependencies()
rules_esbuild_dependencies()

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

load("@aspect_rules_esbuild//esbuild:repositories.bzl", "LATEST_ESBUILD_VERSION", "esbuild_register_toolchains")

esbuild_register_toolchains(
    name = "esbuild",
    esbuild_version = LATEST_ESBUILD_VERSION,
)




