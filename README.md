# PDF Client

## Introduction

This is a python client library for a more pleasant experience with [pdf-server](https://github.com/nathanielove/pdf-server)

## Latest Release

The latest release is pdf_client v1.4, released on 6 Sep 2016.

To install the package using pip:

```bash
$ pip install pdf_client
```

## Quickstart

First, create a configuration file `config.json` in your project directory:

```json
{
  "base_url": "http://<YOUR_DOMAIN>/api/v1/",
  "auth_class": "HTTPBasicAuth",
  "auth_args": ["<MY_USERNAME>", "<MY_PASSWORD>"]
}
```
Then, create a `main.py` and try the following:

```python
from pdf_client import config
from pdf_client.api import book

config.load_from_file('config.json')	# load configuration
book_list = book.List().send_request()	# send HTTP requests using client library
print(book_list)
```

The result will be a `list` of `dict` objects, for example

```python
[{'title': 'Sample Book', 'root_section': 779, 'id': 2}]
```

## The `pdf_client.config` module

### `load_from_file()`

This method loads a json file as global configuration.

There are three fields in the json file:

* `base_url`: the base url of the pdf server. (e.g. "http://127.0.0.1:8000/api/v1/" if you are running the django server on localhost)
* `auth_class` *(optional)*: one of the classes in `request.auth` package - `HTTPBasicAuth`, `HTTPDigestAuth` or `HTTPProxyAuth`
* `auth_args` *(optional)*: arguments to be passed into the constructor of `auth_class`

### Update Configuration at Runtime

There are methods to be called at runtime to load/update the global configuration:

* `set_base_url(base_url)`
* `set_auth(auth)`
* `set_basic_auth(username, password)`, as a shortcut

## The `pdf_client.api` Package

It has four modules:

* `book`
* `section`
* `version`
* `content`

### Module `book`

### Module `section`

### Module `version`

### Module `content`
