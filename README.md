# Cardano Configuration

*DEPRECATED* please don't use this package directly. 
See `cardano-node` or `cardano-db-sync` as the only places that used this functionality.

[![GitHub CI][github-shield]][github-ci]

This package exposes functions to provide git information for Cardano tooling.

Cardano tools support building via `nix` and `cabal`.

When building with `nix` the git executable and git metadata isn't available so the
git revision is embedded as a series of 40 zeros during the build. After the nix build
is finished the executable is patched with the correct git sha. See [set-git-rev.hs][set-git-rev.hs]

For `cabal` the Template Haskell function `gitRev` executes in the context of the current git checkout,
requiring the `git` executable and git metadata is available at compile time. This fails on cross-compiling
ARM executables, for cross-compiling use nix.

To use this library copy the `Cardano.Config.Git.Rev` module into the desired cli project and setup `nix`
to use [set-git-rev.hs][set-git-rev.hs].

[github-shield]: https://github.com/input-output-hk/cardano-config/actions/workflows/haskell.yml/badge.svg
[github-ci]: https://github.com/input-output-hk/cardano-config/actions/workflows/haskell.yml
[set-git-rev.hs]: https://github.com/input-output-hk/iohk-nix/blob/master/overlays/haskell-nix-extra/utils/set-git-rev.hs

