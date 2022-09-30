# OpenCL cross-compilation

This project contains a simple Julia script to
cross-compile OpenCL on different (currently 11)
platforms.

## Installation

Clone this repository and run the following
command in Julia v1.8 or later to install the
`BinaryBuilder.jl` package:

```julia
julia> using Pkg
julia> Pkg.activate("/path/to/cross-platform-opencl")
julia> Pkg.instantiate()
```

## Usage

The following command can be run from the root
directory of the project:

```sh
$ julia --project build_tarballs.jl
```

The option `--project` activates the enviroment
of the folder, which contains the `build_tarballs.jl`
script.

If you want to build OpenCL for a specific platform
not listed in `build_tarballs.jl`, you can
pass the name of the platform in the command line:

```sh
$ julia --project build_tarballs.jl x86_64-linux-musl
```

The available names of platforms supported by `BinaryBuilder.jl`
can be obtained with code below:

```julia
julia> using BinaryBuilder

julia> plats = supported_platforms()
16-element Vector{Platform}:
 Linux i686 {libc=glibc}
 Linux x86_64 {libc=glibc}
 Linux aarch64 {libc=glibc}
 Linux armv6l {call_abi=eabihf, libc=glibc}
 Linux armv7l {call_abi=eabihf, libc=glibc}
 Linux powerpc64le {libc=glibc}
 Linux i686 {libc=musl}
 Linux x86_64 {libc=musl}
 Linux aarch64 {libc=musl}
 Linux armv6l {call_abi=eabihf, libc=musl}
 Linux armv7l {call_abi=eabihf, libc=musl}
 macOS x86_64
 macOS aarch64
 FreeBSD x86_64
 Windows i686
 Windows x86_64

julia> triplet.(plats)
16-element Vector{String}:
 "i686-linux-gnu"
 "x86_64-linux-gnu"
 "aarch64-linux-gnu"
 "armv6l-linux-gnueabihf"
 "armv7l-linux-gnueabihf"
 "powerpc64le-linux-gnu"
 "i686-linux-musl"
 "x86_64-linux-musl"
 "aarch64-linux-musl"
 "armv6l-linux-musleabihf"
 "armv7l-linux-musleabihf"
 "x86_64-apple-darwin"
 "aarch64-apple-darwin"
 "x86_64-unknown-freebsd"
 "i686-w64-mingw32"
 "x86_64-w64-mingw32"
```

For additional options:

```sh
$ julia --project build_tarballs.jl --help
```
