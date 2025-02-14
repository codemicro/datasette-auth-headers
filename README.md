# datasette-auth-headers

[![PyPI](https://img.shields.io/pypi/v/datasette-auth-headers.svg)](https://pypi.org/project/datasette-auth-headers/)
[![Changelog](https://img.shields.io/github/v/release/codemicro/datasette-auth-headers?include_prereleases&label=changelog)](https://github.com/codemicro/datasette-auth-headers/releases)
[![Tests](https://github.com/codemicro/datasette-auth-headers/actions/workflows/test.yml/badge.svg)](https://github.com/codemicro/datasette-auth-headers/actions/workflows/test.yml)
[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](https://github.com/codemicro/datasette-auth-headers/blob/main/LICENSE)

*Authenticate a Datasette instance using headers set by an upstream proxy*

---

This plugin is designed to work when Datasette is being run behind a reverse proxy, such as [Caddy](https://caddyserver.com), that is performing authentication on behalf of the app and setting headers in the upstream request. 

For example, when Caddy and [Authentik's proxy provider](https://docs.goauthentik.io/docs/add-secure-apps/providers/proxy/) are used together with a configuration like so:

```
example.com {
  forward_auth * authentik {
    // ...
  }
  reverse_proxy datasette
}
```

Authentik will set [a number of headers](https://docs.goauthentik.io/docs/add-secure-apps/providers/proxy/#headers) in the upstream request, such as `X-Authentik-User`, to inform us who is authenticated. This plugin uses those headers to create a Datasette actor.

## Installation

Install this plugin in the same environment as Datasette.
```bash
datasette install datasette-auth-headers
```
## Usage

You must configure this plugin on the global level within Datasette. An example configuration that reads the `X-Authentik-User` header and uses it as the actor ID is:

```json
{
  "plugins": {
    "datasette-auth-headers": {
      "id-header-name": "X-Authentik-User"
    }
  }
}
```

`id-header-name` is case-insensitive and is the only configuration option at this time.

**You should not use this plugin with headers that can be set by the end user.** Your reverse proxy must strip/overwrite the headers you configure the plugin with for this to be secure.

## Development

To set up this plugin locally, first checkout the code. Then create a new virtual environment:
```bash
cd datasette-auth-headers
python -m venv venv
source venv/bin/activate
```
Now install the dependencies and test dependencies:
```bash
pip install -e '.[test]'
```
To run the tests:
```bash
python -m pytest
```
