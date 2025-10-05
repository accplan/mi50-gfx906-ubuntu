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
