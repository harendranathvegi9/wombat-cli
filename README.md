# wombat-cli

[![Build Status](https://travis-ci.org/npm/wombat-cli.svg?branch=master)](https://travis-ci.org/npm/wombat-cli) [![Coverage Status](https://coveralls.io/repos/github/npm/wombat-cli/badge.svg?branch=master)](https://coveralls.io/github/npm/wombat-cli?branch=master)

The wombat cli tool.



                 ,.--""""--.._
               ."     .'      `-.
              ;      ;           ;
             '      ;             )
            /     '             . ;
           /     ;     `.        `;
         ,.'     :         .     : )
         ;|\'    :      `./|) \  ;/
         ;| \"  -,-   "-./ |;  ).;
         /\/              \/   );
        :                 \    ;
        :     _      _     ;   )
        `.   \;\    /;/    ;  /
          !    :   :     ,/  ;
           (`. : _ : ,/""   ;
            \\\`"^" ` :    ;
                     (    )
                     ////

```
the helpful wombat tool

Commands:
  hook                control your hooks
  package <package>   see information about the named package
  versions <package>  see all available versions for the named package
  whoami              the username you are authenticated as

Options:
  --registry, -r  the registry configuration to use         [default: "default"]
  --json, -j      print output as json                [boolean] [default: false]
  --help          Show help                                            [boolean]
  --version       show version information                             [boolean]
```

Help is available for each of the supported commands.

You may also do fun things like `wombat ls --depth=0` and `npm` will be invoked.

## configuration

Wombat reads its config from the file `~/.wombatrc`. This file is parsed as [TOML](https://github.com/toml-lang/toml). The defaults look like this:

```toml
[default]
registry = "https://registry.npmjs.org"
api = "https://registry.npmjs.org/-/npm"
```

You can add sections for other registries to talk to and point wombat to them using the name of the config section, or change the default to a registry you use more often. For example:

```toml
[default]
registry = "https://registry.npmjs.org"
api = "https://registry.npmjs.org/-/npm"

[enterprise]
registry = "https://npm-enterprise.private.npmjs.com"
api = "https://api.private.npmjs.com"
```

Then run something like `wombat -r enterprise package @secret/private-package`

## web hooks

```
wombat hook

Commands:
  ls [pkg]                    list your hooks
  add <pkg> <url> <secret>    add a hook to the named package
  update <id> <url> [secret]  update an existing hook
  rm <id>                     remove a hook

Examples:
  wombat hook add lodash https://example.com/webhook my-shared-secret
  wombat hook ls lodash
  wombat hook ls --json
  wombat hook rm id-ers83f
```

## viewing packages

`wombat package yargs` shows you a formatted description of the package meta-data. Pass `--readme` to get the package readme rendered in your terminal as markdown!

`wombat versions yargs` shows you a list of all dist-tags and versions for the named package (in this case, yargs).

## whoami

Find out who you are logged in as for the registry you're using.

## License

ISC
