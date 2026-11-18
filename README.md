# keycloak-discord

Keycloak Social Login extension for Discord.


## Install

Download `keycloak-discord-<version>.jar` from [Releases page](https://github.com/wadahiro/keycloak-discord/releases).
Then deploy it into `$KEYCLOAK_HOME/providers` directory.

### Compatibility

| keycloak-discord | Keycloak        |
|------------------|-----------------|
| 0.7.0 and later  | 26.5.0 and later (built against 26.8.2) |
| 0.6.x            | 26.0.x – 26.4.x |

Keycloak 26.5 changed the broker SPI in a binary-incompatible way. On Keycloak 26.5 or later, 0.6.x still starts, but every Discord login fails with a `NoSuchMethodError`.

### Upgrading

The provider id (`discord`), the mapper id (`discord-user-attribute-mapper`) and the configuration keys (e.g. `allowedGuilds`) are unchanged. Existing identity providers, mappers and linked users keep working without any manual steps:

1. Stop Keycloak.
2. Replace the old `keycloak-discord-*.jar` in `$KEYCLOAK_HOME/providers` with the new one. Keep only one version in the directory.
3. Upgrade Keycloak to 26.5 or later, run `kc.sh build` if you use an optimized build, and start Keycloak.

Upgrade Keycloak and the jar at the same time: 0.6.x does not work on 26.5+, and 0.7.0+ does not work on 26.4 or older.

## Setup

### Discord

Access to [Discord Developer Portal](https://discord.com/developers/applications) and create your application.
You can get Client ID and Client Secret from the created application.

### Keycloak

Note: You don't need to setup the theme in `master` realm from v0.3.0.

1. Add `discord` Identity Provider in the realm which you want to configure.
2. In the `discord` identity provider page, set `Client Id` and `Client Secret`.
3. (Optional) Set Guild Id(s) to allow federation if you want.


## Source Build

Clone this repository and run `mvn package`.
You can see `keycloak-discord-<version>.jar` under `target` directory.


## Licence

[Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0)


## Author

- [Hiroyuki Wada](https://github.com/wadahiro)

