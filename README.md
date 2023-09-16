# `rules_foreign_cc` shared library example

Quick repoduction of an issue I'm seeing where CMake libraries which set a
version don't seem to work as shared libraries.

Based on the example code at https://github.com/bazelbuild/rules_foreign_cc/tree/main/examples/cmake_hello_world_lib

```
bazel test //...
```

Tests (dynamic linking by default) fail with the error:

```
test_libhello: error while loading shared libraries: libhello.so.123: cannot open shared object file: No such file or directory
```

The folder `bazel-bin/shared/copy_libhello` seems to have both `libhello.so` and `libhello.so.123`.
