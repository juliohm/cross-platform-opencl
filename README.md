# OpenCL cross-compilation

This project contains a simple Julia script to
cross-compile OpenCL on different (currently 11)
platforms.

## Installation

Clone this repository and run the following
command to install the `BinaryBuilder.jl`
package in Julia v1.8 or later:

```julia
using Pkg

Pkg.activate("/path/to/cross-platform-opencl")
Pkg.instantiate()
```

## Usage

The following command can be run from the root
directory of the project:

```sh
julia --project --color=yes build_tarballs.jl
```

The option `--project` activates the enviroment
of the folder and the option `--color=yes` enables
colored output.

If you want to build OpenCL for a specific platform
not listed in `build_tarballs.jl`, you can
pass the name of the platform in the command line:

```sh
julia --project --color=yes build_tarballs.jl x86_64-linux-musl
```

The available names of platforms supported by `BinaryBuilder.jl`
can be obtained with code below:

```julia
using BinaryBuilder

plats = supported_platforms()

triplet.(plats)
```
