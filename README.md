# conan+meson+boost

Demonstrating the issue of https://github.com/mesonbuild/meson/issues/5438

What does not work:

```
mkdir build
cd build
conan install ..
meson
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
