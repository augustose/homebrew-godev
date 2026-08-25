# homebrew-godev

Homebrew tap for [godev](https://github.com/augustose/godev) — navigate 100+
development projects in seconds with fuzzy search and Git awareness.

## Install

```zsh
brew install augustose/godev/godev
```

Then set up the shell integration, once:

```zsh
godev --init --install && source ~/.zshrc
```

### Why the extra step?

godev changes your shell's working directory, and a child process cannot change
its parent's working directory — so it needs a function defined *in* your shell.
Homebrew never edits your `~/.zshrc` by policy, so `godev --init --install` does
it for you: it backs up the file, adds one line, and validates the result before
replacing anything. Cancelling leaves it untouched.

To do it by hand instead, add this to your `~/.zshrc`:

```zsh
eval "$(godev --init zsh)"
```

## Upgrade

```zsh
brew upgrade godev
```

Homebrew-managed installs do not self-update. `godev --update` will tell you a
new version exists and point you here rather than writing into the Cellar.

## Issues

Report bugs against the [main repository](https://github.com/augustose/godev/issues).
