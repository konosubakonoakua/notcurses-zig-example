
# Notcurses Zig example

[Notcurses](https://notcurses.com/) is a moderm library for building terminal UIs with advanced graphics support.

This is a demo showing how to use it with [Zig](https://ziglang.org/) programming language.  
Thanks to Zig's seamless C interop the library can be used directly without wrapper bindings.

![Notcurses Zig demo](https://user-images.githubusercontent.com/755611/114319180-d83ac400-9aff-11eb-8b50-3e9a388b91c7.png)

### Dependencies
1. Install [Notcurses dependencies](https://github.com/dankamongmen/notcurses/blob/master/INSTALL.md)
  - using [Nix](https://nixos.org/):  
  `nix-shell`
  - for Debian/Ubuntu:
      ```sh
      sudo apt-get install build-essential cmake doctest-dev \
      libavdevice-dev libdeflate-dev libgpm-dev libncurses-dev \
      libqrcodegen-dev libswscale-dev libunistring-dev pandoc pkg-config
      ```
 
2. [Install Zig](https://ziglang.org/download/) (version 0.11.0)
3. Get Notcurses to compile from sources (since distributions don't often package latest versions):
    ```sh
    git submodule init && git submodule update
    mkdir -p deps/notcurses/build
    pushd deps/notcurses/build
    cmake -DUSE_MULTIMEDIA=none -DUSE_PANDOC=OFF ..
    popd
    # We just need `cmake` to generate some headers, no need to actually `make` since rest will be handled by Zig
    # In case of errors, try `git checkout v3.0.9` and re-run cmake as I tested it with this version.
    ```

### Build and run

```sh
# Build and run the demo:
zig build run
# build and run the binary separately:
zig build && ./zig-cache/run/demo
```

### Related

