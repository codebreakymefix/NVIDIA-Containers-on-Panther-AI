# Loading NVIDIA Containers on Panther AI

1. Loads Apptainer module.

	```bash
 	module load apptainer/1.3.4-gcc-14.2.0-spxhran
 	```
 
	> **Info:** In HPC environments, Apptainer is used because it’s a rootless alternative to Docker.
	
2. Pulls the NVIDIA PyTorch NGC container image.
	
 	```bash
  	apptainer pull docker://nvcr.io/nvidia/pytorch:23.08-py3
   ```

	> **Tip:** You can find more NVIDIA NGC container images [here](https://catalog.ngc.nvidia.com/containers?filters=&orderBy=weightPopularDESC&query=&page=&pageSize=).

3. We run an interactive terminal in one of the GPU nodes.
	
 	```bash
	srun -w gpu03 -p gpu1 --pty bash -i
  	```

	> **Tip:** You can check if you are in the GPU Node if there is 'gpu03' after your username in the terminal.

4. Unload/reload different Apptainer build.
	
 	```bash
	module unload apptainer
  	module load apptainer/1.3.4-gcc-14.2.0-g7o5w4g
  	```

 5. Check if PyTorch is installed.

	```bash
   	apptainer exec --nv --cleanenv pytorch_23.08-py3.sif python -c "import torch; print(torch.__version__, torch.version.cuda)"
	```

6. _(Optional)_ You can open up an interactive terminal for quick installations.
	
 	```bash
	apptainer shell --nv --cleanenv pytorch_23.08-py3.sif
	```
## Running Containers on SBATCH Files

- Just change the path ('pathhere/pythonfile.py') to your python file.
 	```bash
  	module load apptainer/1.3.4-gcc-14.2.0-g7o5w4g
  	apptainer exec --nv --cleanenv pytorch_23.08-py3.sif python pathhere/pythonfile.py"
	```
	> **Info:** Did not test this command.


