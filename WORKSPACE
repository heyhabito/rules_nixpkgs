workspace(name = "io_tweag_rules_nixpkgs")

load("//nixpkgs:nixpkgs.bzl", "nixpkgs_git_repository", "nixpkgs_package")

# For tests

nixpkgs_package(name = "hello", repositories = { "//:nix/default.nix": "nixpkgs" })

nixpkgs_package(
  name = "expr-test",
  nix_file_content = "let pkgs = import <nixpkgs> {}; in pkgs.hello",
  repositories = { "//:nix/default.nix": "nixpkgs" }
)

nixpkgs_package(
  name = "attribute-test",
  attribute_path = "hello",
  repositories = { "//:nix/default.nix": "nixpkgs" }
)

nixpkgs_package(
  name = "expr-attribute-test",
  nix_file_content = "import <nixpkgs> {}",
  attribute_path = "hello",
  repositories = { "//:nix/default.nix": "nixpkgs" },
)

nixpkgs_package(
  name = "nix-file-test",
  nix_file = "//tests:nixpkgs.nix",
  attribute_path = "hello",
  repositories = { "//:nix/default.nix": "nixpkgs" },
)

nixpkgs_package(
  name = "nix-file-deps-test",
  nix_file = "//tests:hello.nix",
  nix_file_deps = ["//tests:pkgname.nix"],
  repositories = { "//:nix/default.nix": "nixpkgs" },
)
