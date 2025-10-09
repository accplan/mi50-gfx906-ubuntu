It seems like ROCm 6.4-7.0 still support gfx906 but one needs to compile TensileLibrary for gfx906 manually (or download it from somewhere else).
Instructions can be found in this issue: https://github.com/ROCm/ROCm/issues/4625

- rocblas still supports gfx906, you can build from source to get the TensileLibrary file for gfx906 for now. You can edit [this](https://github.com/ROCm/rocBLAS/blob/80e5394d6a68901ce48b03da47b33b1e69d58be7/CMakeLists.txt#L115C12-L115C13) line to only build for gfx906, this should speed up the build.

- Just for anyone who won't be able to build from source. I think it is possible to take TensileLibrary_lazy_gfx906.dat from this package: https://archlinux.org/packages/extra/x86_64/rocblas/
  Download it and extract.

## Tensile
1. git clone https://github.com/ROCmSoftwarePlatform/Tensile.git
2. cd Tensile
3. git checkout (ROCm version)

## rocBLAS
1. git clone https://github.com/ROCmSoftwarePlatform/rocBLAS.git
2. cd rocBLAS
3. git checkout (ROCm version)
4. ./install.sh --no_hipblaslt --architecture "gfx906;gfx906:xnack-;gfx906:xnack+" -j14 -t (Tensile directory)
5. compiled TensileLibrary files should be in ./build/release/rocblas-install/lib/rocblas/library
