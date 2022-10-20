---
title: "authelia crypto hash generate argon2"
description: "Reference for the authelia crypto hash generate argon2 command."
lead: ""
date: 2022-10-17T21:51:59+11:00
draft: false
images: []
menu:
  reference:
    parent: "cli-authelia"
weight: 330
toc: true
---

## authelia crypto hash generate argon2

Generate cryptographic Argon2 hash digests

### Synopsis

Generate cryptographic Argon2 hash digests.

This subcommand allows generating cryptographic Argon2 hash digests.

```
authelia crypto hash generate argon2 [flags]
```

### Examples

```
authelia crypto hash generate argon2 --help
```

### Options

```
  -h, --help              help for argon2
  -i, --iterations int    number of iterations (default 3)
  -k, --key-size int      key size in bytes (default 32)
  -m, --memory int        memory in kibibytes (default 65536)
  -p, --parallelism int   parallelism or threads (default 4)
      --profile string    profile to use, options are low-memory and recommended
  -s, --salt-size int     salt size in bytes (default 16)
  -v, --variant string    variant, options are 'argon2id', 'argon2i', and 'argon2d' (default "argon2id")
```

### Options inherited from parent commands

```
  -c, --config strings             configuration files to load (default [configuration.yml])
      --no-confirm                 skip the password confirmation prompt
      --password string            manually supply the password rather than using the terminal prompt
      --random                     uses a randomly generated password
      --random.characters string   sets the explicit characters for the random string
      --random.charset string      sets the charset for the random password, options are 'ascii', 'alphanumeric', 'alphabetic', 'numeric', and 'numeric-hex' (default "alphanumeric")
      --random.length int          when using a randomly generated password it configures the length (default 72)
```

### SEE ALSO

* [authelia crypto hash generate](authelia_crypto_hash_generate.md)	 - Generate cryptographic hash digests
