# datasette-auth-headers

[![PyPI](https://img.shields.io/pypi/v/datasette-auth-headers.svg)](https://pypi.org/project/datasette-auth-headers/)
[![Changelog](https://img.shields.io/github/v/release/codemicro/datasette-auth-headers?include_prereleases&label=changelog)](https://github.com/codemicro/datasette-auth-headers/releases)
[![Tests](https://github.com/codemicro/datasette-auth-headers/actions/workflows/test.yml/badge.svg)](https://github.com/codemicro/datasette-auth-headers/actions/workflows/test.yml)
[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](https://github.com/codemicro/datasette-auth-headers/blob/main/LICENSE)

Authenticate a Datasette instance using headers set by an upstream proxy

## Installation

Install this plugin in the same environment as Datasette.
```bash
datasette install datasette-auth-headers
```
## Usage

Usage instructions go here.

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
