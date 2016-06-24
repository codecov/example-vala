# Codecov Vala Example

[![codecov](https://codecov.io/gh/arteymix/example-vala/branch/master/graph/badge.svg)](https://codecov.io/gh/arteymix/example-vala)

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

