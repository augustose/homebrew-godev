# homebrew-godev

> [!WARNING]
> **This tap is deprecated.** The godev formula moved to the consolidated tap
> [augustose/homebrew-tap](https://github.com/augustose/homebrew-tap). This
> repository is frozen at v2.8.1 and will receive no further updates.
>
> To migrate:
>
> ```zsh
> brew uninstall godev && brew untap augustose/godev
> brew trust augustose/tap && brew install augustose/tap/godev
> ```
>
> Your settings in `~/.config/godev/` are untouched by the reinstall.

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
eval "$(command godev --init zsh)"
```

### Upgrading from a pre-2.7.0 script install

If you installed godev with the `curl | zsh` installer before 2.7.0, your shell
still has the old wrapper function, and it calls `~/.local/bin/godev` by absolute
path. That binary has no `--init` flag and would read it as a project name, so
reach the Homebrew binary directly, once:

```zsh
"$(brew --prefix)/bin/godev" --init --install
rm ~/.local/bin/godev
source ~/.zshrc
```

Your settings in `~/.config/godev/` are untouched — the Homebrew build reads the
same path.

## Upgrade

```zsh
brew upgrade godev
```

Homebrew-managed installs do not self-update. `godev --update` will tell you a
new version exists and point you here rather than writing into the Cellar.

## Issues

Report bugs against the [main repository](https://github.com/augustose/godev/issues).
