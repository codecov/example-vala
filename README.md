# [Codecov][1] Vala Example
## Guide
### Travis Setup

Add to your `.travis.yml` file.
```yml
language: c
after_success:
  - bash <(curl -s https://codecov.io/bash)
```
### Produce Coverage Reports

Since Vala translate to C, [the usage same directives for C/C++](https://github.com/codecov/example-c)
apply. The ``--ccode`` and ``--debug`` flags have to be specified so that the
C coverage can be properly mapped to the original sources.

```bash
valac --debug --ccode hello.vala
gcc $(pkg-config --cflags --libs glib-2.0 gobject-2.0) -ftest-coverage -fprofile-arcs -o hello hello.c
./hello
gcov hello.vala
```

## Meson

To enable coverage with [Meson][5], specify the `-D b_coverage=true` project option.

```bash
mkdir build && cd build
meson -D b_coverage=true ..
ninja
ninja test
```

## Caveats
### Private Repos
Add to your `.travis.yml` file.
```yml
after_success:
  - bash <(curl -s https://codecov.io/bash) -t uuid-repo-token
```

1. More documentation at https://docs.codecov.io
2. Configure codecov through the `codecov.yml`  https://docs.codecov.io/docs/codecov-yaml

We are happy to help if you have any questions. Please contact email our Support at [support@codecov.io](mailto:support@codecov.io)

[1]: https://codecov.io/
[5]: http://mesonbuild.com/
