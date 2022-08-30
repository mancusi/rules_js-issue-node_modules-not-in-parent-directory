workspace(
    # see https://docs.bazel.build/versions/main/skylark/deploying.html#workspace
    name = "node_modules_not_in_parent_directory",
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "aspect_rules_js",
    sha256 = "25bcb082d49616ac2da538bf7bdd33a9730c8884edbec787fec83db07e4f7f16",
    strip_prefix = "rules_js-1.1.0",
    url = "https://github.com/aspect-build/rules_js/archive/refs/tags/v1.1.0.tar.gz",
)

load("@aspect_rules_js//js:repositories.bzl", "rules_js_dependencies")

rules_js_dependencies()

load("@rules_nodejs//nodejs:repositories.bzl", "DEFAULT_NODE_VERSION", "nodejs_register_toolchains")

nodejs_register_toolchains(
    name = "nodejs",
    node_version = DEFAULT_NODE_VERSION,
)

load("@aspect_rules_js//npm:npm_import.bzl", "npm_translate_lock")

npm_translate_lock(
    name = "npm",
    pnpm_lock = "//js:pnpm-lock.yaml",
)

load("@npm//:repositories.bzl", "npm_repositories")

npm_repositories()
