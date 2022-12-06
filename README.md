# `ycp`: Just a tool to switch Yandex Cloud Profiles

![Proudly written in Bash](https://img.shields.io/badge/written%20in-bash-ff69b4.svg)

This repository provides both `ycp` tools.
[Install &rarr;](#installation)

## What is `ycp`?

**ycp** is a tool to switch between profiles on yc faster.<br/>

### Examples

```sh
# switch to another profile
% ycp freehck-terraform-prod
Profile 'freehck-terraform-prod' activated

# switch back to previous profile
% ycp -
Profile 'freehck-terraform-dev' activated

# get current yandex cloud profile
% ycp -c
freehck-terraform-dev
```

If you have [`fzf`](https://github.com/junegunn/fzf) installed, you can also
**interactively** select a profile, or fuzzy-search by typing a few
characters. To learn more, read [interactive mode &rarr;](#interactive-mode)

-----

## Installation

Stable versions of `ycp` are small bash scripts that you can find in this repository.

**Installation options:**

- [manually (macOS & Linux)](#manual-installation-macos-and-linux)

### Manual Installation (macOS and Linux)

Since `ycp` is written in Bash, you should be able to install them to any POSIX
environment that has Bash installed.

- Download the `ycp` script.
- Either:
  - save it to somewhere in your `PATH`,
  - or save them to a directory, then create symlinks to `ycp` from
    somewhere in your `PATH`, like `/usr/local/bin`
- Make `ycp` executable (`chmod +x ...`)

Example installation steps:

``` bash
sudo git clone https://github.com/almaops/ycp /opt/ycp
sudo ln -s /opt/ycp/ycp /usr/local/bin/ycp
```

-----

### Interactive mode

If you want `ycp` command to present you an interactive menu with fuzzy searching,
you just need to [install `fzf`](https://github.com/junegunn/fzf) in your `$PATH`.

If you have `fzf` installed, but want to opt out of using this feature, set the
environment variable `YCP_IGNORE_FZF=1`.

If you want to keep `fzf` interactive mode but need the default behavior of the
command, you can do it by piping the output to another command (e.g. `ycp |
cat `).

-----

### Customizing colors

If you like to customize the colors indicating the current profile,
set the environment variables `YCP_CURRENT_FGCOLOR` and 
`YCP_CURRENT_BGCOLOR` (refer color codes
[here](https://linux.101hacks.com/ps1-examples/prompt-color-using-tput/)):

```sh
export YCP_CURRENT_FGCOLOR=$(tput setaf 6) # blue text
export YCP_CURRENT_BGCOLOR=$(tput setab 7) # white background
```

Colors in the output can be disabled by setting the
[`NO_COLOR`](https://no-color.org/) environment variable.