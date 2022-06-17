---
title: "Migration"
description: "Information regarding configuration migration."
lead: "An introduction into configuring Authelia."
date: 2022-03-20T12:52:27+11:00
draft: false
images: []
menu:
  configuration:
    parent: "prologue"
weight: 100300
toc: true
aliases:
  - /docs/configuration/migration.html
---

This section documents changes in the configuration which may require manual migration by the administrator. Typically
this only occurs when a configuration key is renamed or moved to a more appropriate location.

## Format

The migrations are formatted in a table with the old key and the new key. Periods indicate a different section which can
be represented in [YAML] as a dictionary i.e. it's indented.

In our table `server.host` with a value of `0.0.0.0` is represented in [YAML] like this:

```yaml
server:
  host: 0.0.0.0
```

## Policy

Our deprecation policy for configuration keys is 3 minor versions. For example if a configuration option is deprecated
in version 4.30.0, it will remain as a warning for 4.30.x, 4.31.x, and 4.32.x; then it will become a fatal error in
4.33.0+.

## Migrations

### 4.33.0

The options deprecated in version [4.30.0](#4300) have been fully removed as per our deprecation policy and warnings
logged for users.

### 4.30.0

The following changes occurred in 4.30.0:

| Previous Key  |        New Key         |
|:-------------:|:----------------------:|
|     host      |      server.host       |
|     port      |      server.port       |
|    tls_key    |     server.tls.key     |
|   tls_cert    | server.tls.certificate |
|   log_level   |       log.level        |
| log_file_path |     log.file_path      |
|  log_format   |       log.format       |

*__Please Note:__ you can no longer define secrets for providers that you are not using. For example if you're using the
[filesystem notifier](../notifications/introduction.md) you must ensure that the `AUTHELIA_NOTIFIER_SMTP_PASSWORD_FILE`
environment variable or other environment variables set. This also applies to other providers like
[storage](../storage/introduction.md) and [authentication backend](../first-factor/introduction.md).*

#### Kubernetes 4.30.0

*__Please Note:__ if you're using Authelia with Kubernetes and are not using the provided
[helm chart](https://charts.authelia.com) you will be required to
[configure the enableServiceLinks](../../integration/kubernetes/introduction/index.md#enable-service-links) option.*

### 4.25.0

The following changes occurred in 4.25.0:

|                  Previous Key                   |                     New Key                     |
|:-----------------------------------------------:|:-----------------------------------------------:|
|   authentication_backend.ldap.tls.skip_verify   |   authentication_backend.ldap.tls.skip_verify   |
| authentication_backend.ldap.minimum_tls_version | authentication_backend.ldap.tls.minimum_version |
|        notifier.smtp.disable_verify_cert        |          notifier.smtp.tls.skip_verify          |
|           notifier.smtp.trusted_cert            |             certificates_directory              |

*__Please Note:__ `certificates_directory` is not a direct replacement for the `notifier.smtp.trusted_cert`, instead
of being the path to a specific file it is a path to a directory containing certificates trusted by Authelia. This
affects other services like LDAP as well.*

### 4.7.0

The following changes occurred in 4.7.0:

| Previous Key |  New Key  |
|:------------:|:---------:|
|  logs_level  | log_level |
|  logs_file   | log_file  |

*__Please Note:__ The new keys also changed in [4.30.0](#4.30.0) so you will need to update them to the new values if you
are using [4.30.0](#4.30.0) or newer instead of the new keys listed here.*

[YAML]: https://yaml.org/