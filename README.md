# 1Password CLI Sanity Wrapper

The 1Password CLI is almost good, except that you have to set an environment
variable everywhere. If you have more than one terminal open, this is a gigantic
pain in the ass.

This is a little wrapper script that will auto-log-in when you run commands,
and will store/load session tokens from within the `$HOME/.op` directory.

You can use it just like `op`. Have fun.

## Installation

1. Install the 1Password CLI: https://1password.com/downloads/command-line/ somewhere in your `$PATH`
2. Install this tool somewhere in your path, too


## Usage

1. Sign in to some accounts with `op signin <domain> <username>`
2. Use `sop` like you would use `op`. The first time it's used, it will prompt
   you for a password. Subsequently, it should be smart enough to use the
   stored-and-validated session token.


## Caveats

This tool is not yet smart enough to wrap `sop signin` to store the token to
avoid a secondary login.

Because this tool tries to check current token status on every use, it will
incur a minor amount of overhead -- a second HTTP request -- per command usage.
Not much I can do about that, sorry.
