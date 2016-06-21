# Bash Packages Cask

Bash Packages are part of the bCLI system (see: https://github.com/jim-cooley/bash.cli).

Packages in the Cask are those that are under development and may need to ferment a little bit more.

# What is bCLI?

bCLI is a basic package manager for Bash.  It enables you to collect your favorite commands, scripts, aliases, functions, etc together into packages that can be managed atomically under the Bash command shell.  

Currently, this is running on OSX and has not been tested on other platforms.  

It differs from the Brew package manager in that 'packages' need to be executed within the context of the host shell in order to be effected (definitions cannot be exported from a subshell).  It does build a cached state of itself (~/_bCLI.cache) for fast loading or manual hacking, but better to just hack in a regular shell session and use the 'bCLI save' command.

# What is a 'Package'?

A package is a shell script that will be executed in context of the parent shell (using 'source').  It must have a '[packagename].package' entry point and install script.  Other files in the package directory (most notably executable files) will be soft-linked to your $CLIBIN directory.  This enables easy updating via 'git' into your repository directory.

# Installation

bCLI is self-contained and easily installed.  Just:
* 'Clone' the repository
* cd to the root on the newly cloned project
* execute: ./install (path to put bCLI root/bin, inc, etc directories)
* done

# Running bCLI
bCLI is automatically added to your ```.bashrc``` file and run at startup of a new shell.  It can be configured by modifying or adding definitions to the ~/_bcli.cfg file.

# bCLI Commands:
bCLI can be managed by using the 'bcli' command (function):

```sh
bcli, version: 0.50

  bcli: {-h} [ build | install {-p} package | save ]

  options:
    -h | --help         = print help on help

  parameters:
    (b) build   - build things (alias for 'make')
    (c) clean   - clean environment
    (h) help    - bcli help system search
    (i) install - install a package or project
    (l) list    - list things
    (m) make    - make things
    (p) print   - bcli print facility (definitions, variables, etc)
    (r) run     - run things
    (s) save    - save the current environment
```

Additionally, there are several aliases added with the 'bcli' package.  Type:
```h --package bcli```
for more information and an example of using the new bCLI ```help``` system.

# You said bCLI Help System?

Yes, bCLI adds a help system 'see bash.package/help' that quickly searches your environment, aliases, manpages, local 'help' as well as installable packages .help files and other sources.  It can be a one-stop quick lookup.

type ```h``` and hit <<enter>> for more information regarding sub commands.
 
