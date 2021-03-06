
The current version of broot works on linux, mac and windows (win 10+).


!!! Note
	**Windows users:** broot may need additional rights at first use in order to write its configuration file.
	Some users on Windows also report problems with the colon. Remember that a space can be used instead of a colon.
	You should also use the new Powershell terminal and not the old cmd.exe which isn't supported.

!!! Note
	If you use cargo and there's a compilation error, it usually means you have an old version of the compiler, and you should update it (for example with `rustup update`).

# From precompiled binaries

Binaries are made available at every release in [download](https://dystroy.org/broot/download).

Direct links:

Target|Files
-|-
Linux | [x86_64-linux](https://dystroy.org/broot/download/x86_64-linux/broot)
Linux/musl | [x86_64-unknown-linux-musl](https://dystroy.org/broot/download/x86_64-unknown-linux-musl/broot)
Raspberry | [armv7-unknown-linux-gnueabihf](https://dystroy.org/broot/download/armv7-unknown-linux-gnueabihf/broot)
Windows 10+ | [x86_64-pc-windows-gnu](https://dystroy.org/broot/download/x86_64-pc-windows-gnu/broot.exe)
Shell completion | [completion/](https://dystroy.org/broot/download/completion/)

You may download previous releases on [GitHub releases](https://github.com/Canop/broot/releases).

When you download executable files, you'll have to ensure the shell can find them. An easy solution on linux is for example to put them in `/usr/local/bin`. You may also have to set them executable using `chmod +x broot`.

# From crates.io

You'll need to have the [Rust development environment](https://www.rust-lang.org/tools/install) installed.

Once it's installed, use cargo to install broot:

    cargo install broot

# From source

You'll need to have the [Rust development environment](https://www.rust-lang.org/tools/install) installed.

Fetch the [Canop/broot](https://github.com/Canop/broot) repository, move to the broot directory, then run

    cargo install --path .


# Homebrew

If you're using [homebrew](https://brew.sh/), you can use the `brew install` command:

    brew install broot

*note: the brew formula is maintained by a third party and may be less up to date.*

# APT / Deb

Ubuntu and Debian users may use this apt repository: [https://packages.azlux.fr/](https://packages.azlux.fr/)

*note: this repository is also maintained by a third party.*

# Installation Completion : the `br` shell function

broot is convenient to find a directory then `cd` to it, which is done using <kbd>alt</kbd><kbd>enter</kbd> or `:cd`.

But broot needs a companion function in the shell in order to be able to change directory.

## Automatic shell function installation

This is normally the easiest solution and it's safe.

When you start broot, it checks whether the `br` shell function seems to have been installed (or
to have been refused). If needed, and if the used shell seems compatible (supported shells today are bash, zsh and fish),
then broot asks the permission to register this shell function.

When it's done, you can do `br` to launch broot, and typing <kbd>alt</kbd><kbd>enter</kbd> will cd for you.

## Retry the automatic installation

If you have messed with the configuration files, you might want to have the shell function reinstalled.

In order to do this, either remove all broot config files, or launch `broot --install`.

You can also use the `--install` argument when you first refused and then decided you want it installed.

## Manual shell function installation

If you prefer to manage the function sourcing yourself, or to automate the installation your way, or if you use an unsupported configuration, you still can get some help of broot:

`broot --print-shell-function bash` (you can replace `bash` with either `zsh` or `fish`) outputs a recommended shell function.

`broot --set-install-state installed` tells broot the `br` function is installed (other possible values are `undefined` and `refused`).

## `br` alias for Nushell

As a shortcut for [Nushell](https://www.nushell.sh/), define the following alias:

    alias br [] { broot | trim | cd $it }

You can bind this command to a key sequence in the [configuration file](../conf_file):

```toml
[[verbs]]
key = "alt-c"
shortcut = "pp"
execution = ":print_path"
```

# Fix the colors

Broot's initial colors ensure that everything is readable whathever your settings.
But you may want to have something more similar to your usual terminal colors, or maybe to define the whole skin.

You should probably have a look at [changing the skin](../skins) as your next step.

