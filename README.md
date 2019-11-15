# Fzy as a Zsh Package

Zplugin can use the NPM package registry to automatically:

- get the plugin's Git repository,
- get the list of the recommended ices for the plugin,
- there can be multiple lists of ices,
- the ice lists are stored in *profiles*; there's at least one profile, *default*,
- the ices can be selectively overriden.

```zsh
# Download the package with the default ice list
zplugin pack for fzy

# Download the package with the bin-gem-node annex-utilizing ice list
zplugin pack"bgn" for fzy
```

## Default Profile

Provides the fuzzy finder via Makefile-installation of the `fzy` binary under
`$ZPFX/bin`.

```zsh
zplugin wait"1" lucid as"program" pick"$ZPFX/bin/fzy*" \
    atclone"cp contrib/fzy-* $ZPFX/bin/" \
    make"!PREFIX=$ZPFX install"
```

## Bin-Gem-Node Profile

Provides the fuzzy finder via *shims*, i.e.: automatic forwarder scripts created
under `$ZPFX/bin` (which is added to the `$PATH` by default).

```zsh
zplugin wait"1" lucid as"null" make sbin"fzy;contrib/fzy-*"
```

<!-- vim:set ft=markdown tw=80 fo+=an1 autoindent: -->
