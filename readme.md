1. Loads the module Apptainer. 
	<pre>
	```module load apptainer/1.3.4-gcc-14.2.0-spxhran```
	</pre>
 
	> **Info:** Apptainer is an alternative from Docker. Apptainer are normally used in HPC environment because their containers do not require root access privileges unlike Docker.
	
2. Pulls NVIDIA Pytorch docker container.
	
 	```apptainer pull docker://nvcr.io/nvidia/pytorch:23.08-py3```

	> **Tip:** You can find more NVIDIA Docker containers [here](https://catalog.ngc.nvidia.com/containers?filters=&orderBy=weightPopularDESC&query=&page=&pageSize=).

3. We run an interactive terminal in one of the GPU nodes.
	
 	```srun -w gpu03 -p gpu1 --pty bash -i```

	> **Tip:** You can check if you are in the GPU by just seeing if there is 'gpu03' after your username in the terminal.

4. Unload/reload different Apptainer build.
	
 	```module unload apptainer```

	```module load apptainer/1.3.4-gcc-14.2.0-g7o5w4g```

6. Check if PyTorch is installed.

   ```apptainer exec --nv --cleanenv pytorch_23.08-py3.sif python -c "import torch; print(torch.__version__, torch.version.cuda)"```

> 	**Tip:** This is how you run python in the sbatch file, just replace everything after `python` with the path to your python file.

6. (Optional) You can open up an interactive terminal in case you need to do some quick installations.
	
 	```apptainer shell --nv --cleanenv pytorch_23.08-py3.sif```
