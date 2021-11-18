# Deprecated

❗ All zinit-packages have been migrated to https://github.com/zdharma-continuum/zinit-packages
You'll find the source for this here package in https://github.com/zdharma-continuum/zinit-packages/tree/HEAD/fzy
# jhawthorn/fzy as a Zsh package

##### Homepage link: [jhawthorn/fzy](https://github.com/jhawthorn/fzy)

| **Package source:** | Tarball | Git | Node | Gem |
|:-------------------:|:-------:|:---:|:----:|:---:|
| **Status:**         |    + <br> (default) | + | – |  –  |

[Zplugin](https://github.com/zdharma-continuum/zinit) can use the NPM package registry to automatically:

- get the plugin's Git repository OR release-package URL,
- get the list of the recommended ices for the plugin,
    - there can be multiple lists of ices,
    - the ice lists are stored in *profiles*; there's at least one profile, *default*,
    - the ices can be selectively overriden.

Example invocations that'll install
[jhawthorn/fzy](https://github.com/jhawthorn/fzy) either from the release
archive or from Git repository:

```zsh
# Download the package with the default ice list
zplugin pack for fzy

# Download the package with the bin-gem-node annex-utilizing ice list
zplugin pack"bgn" for fzy

# Download with the bin-gem-node annex-utilizing ice list FROM GIT REPOSITORY
zplugin pack"bgn" git for fzy

# Download normal ice list and override atclone'' ice to skip the contrib scripts
zplugin pack"bgn" atclone'' for fzy
```

## Default Profile

Provides the fuzzy finder via Makefile-installation of the `fzy` binary under
`$ZPFX/bin`.

```zsh
zplugin lucid as"program" pick"$ZPFX/bin/fzy*" \
    atclone"cp contrib/fzy-* $ZPFX/bin" \
    make"PREFIX=$ZPFX install" \
    …
```

## Bin-Gem-Node Profile

Provides the fuzzy finder via *shims*, i.e.: automatic forwarder scripts created
under `$ZPFX/bin` (which is added to the `$PATH` by default). It needs the
[bin-gem-node](https://github.com/zplugin/z-a-bin-gem-node) annex.

```zsh
zplugin lucid as"null" make sbin"fzy;contrib/fzy-*" …
```

<!-- vim:set ft=markdown tw=80 fo+=an1 autoindent: -->
