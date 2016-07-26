# Codecov Vala Example

[![Build Status](https://travis-ci.org/codecov/example-vala.svg?branch=master)](https://travis-ci.org/codecov/example-vala)
[![codecov](https://codecov.io/gh/codecov/example-vala/branch/master/graph/badge.svg)](https://codecov.io/gh/codecov/example-vala)

| [https://codecov.io][1] | [@codecov][2] | [hello@codecov.io][3] |
| ----------------------- | ------------- | --------------------- |

This repository serves as an **example** on how to use [Codecov Global][4] for Vala.

# Usage

Since Vala translate to C, [the usage same directives for C/C++](https://github.com/codecov/example-c)
apply. The ``--ccode`` and ``--debug`` flags have to be specified so that the
C coverage can be properly mapped to the original sources.

```bash
valac --debug --ccode hello.vala
gcc $(pkg-config --cflags --libs glib-2.0 gobject-2.0) -ftest-coverage -fprofile-arcs -o hello hello.c
./hello
gcov hello.vala
```

# Travis CI

Add to your `.travis.yml` file.
```yml
after_success:
  - bash <(curl -s https://codecov.io/bash)
```

> All other CI you can simply run `bash <(curl -s https://codecov.io/bash)`.

## Private Repos

Include your Codecov upload token found in the repository settings page on Codecov
```yml
after_success:
  - bash <(curl -s https://codecov.io/bash) -t repo-upload-token
```

View source and learn more about [Codecov Global Uploader][4]

[1]: https://codecov.io/
[2]: https://twitter.com/codecov
[3]: mailto:hello@codecov.io
[4]: https://github.com/codecov/codecov-bash
