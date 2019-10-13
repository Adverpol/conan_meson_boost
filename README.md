# conan+meson+boost

Demonstrating the issue of https://github.com/mesonbuild/meson/issues/5438

What does not work:

```
mkdir build
cd build
conan install ..

export PKG_CONFIG_PATH=$(realpath ../build/)
meson
```

Error from meson:

```
Run-time dependency Boost found: NO 

meson.build:3:0: ERROR: Dependency "boost" not found
```

what does work:

```
mkdir build
cd build
conan install ..

export PKG_CONFIG_PATH=$(realpath ../build/)
export BOOST_ROOT=$(pkg-config --variable=prefix boost)
meson
```
