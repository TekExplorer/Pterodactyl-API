# Pterodactyl API Documentation
This repository includes the documentation for the [Pterodactyl panel](https://pterodactyl.io) API.
The documentation, files of which are in this repository,
is hosted at [api.ptero.sh](https://api.ptero.sh/#).

# Structure
This repository is structures in two main parts:
## OpenAPI spec
The OpenAPI specifications (the Client API [/api/client] and the Application [/api/application] specifications)
are contained in the [`reference`](./reference) directory.
## Articles
The articles are an extension of the OpenAPI spec,
and are additional documentation for, for example, the WebSocket API.
Currently there is one article:
- [WebSocket API](./docs/Server-Websockets.md)

# Libraries
This list includes libraries that help developers interact with the Pterodactyl API. \
More entries will be added soon.

Kotlin/Java:
- **KOTLIN ONLY, uses Coroutines** [pterodactyl-kt](https://github.com/TeamGloryx/pterodactyl-kt)

Dart:
- The library by the one and only, TekExplorer - [`dartactyl`](https://github.com/TekExplorer/dartactyl)

# Contributing
This repository's OpenAPI spec and articles are edited using [Stoplight Studio](https://stoplight.io/studio).
