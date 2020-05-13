# Fullwave 2D GPU 
  
To run it on **ultrasound-gpu queue of DCC**:

1. prepare a repository with all the fullwave essential `*.dat` files (like for `try6_nomex`) with the `FullWave2D_PGI_19.10_CUDA_9.1_20200512.gpu_volta` inside the repository instead of `try6_nomex`

1. Login to dcc-slogin-01 (not 02, 03 etc, the compiler is node locked).

1. Transfer the repository to DCC.

1. To try it interactively use something like: `srun -p ultrasound-gpu --gres=gpu:1 -c6 --pty bash -i `

1. Or, a sbatch file, with contents something like:


```
#!/bin/bash
#SBATCH --partition=ultrasound-gpu
#SBATCH --output=Output.txt
#SBATCH --nodes=1
#SBATCH --gres=gpu:1
#SBATCH --mem=2G
#SBATCH --time=02:00:00
rm genout.dat

module load CUDA/9.1
module load PGI-compiler/19.10

srun ./FullWave2D_PGI_19.10_CUDA_9.1_20200406.gpu_volta
```

