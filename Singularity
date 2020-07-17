Bootstrap: docker
From: marcchpc/pytorch_cuda9

%environment
  # use bash as default shell
  SHELL=/bin/bash
  export SHELL

  # add CUDA paths
  CPATH="/usr/local/cuda/include:$CPATH"
  PATH="/usr/local/cuda/bin:$PATH"
  LD_LIBRARY_PATH="/usr/local/cuda/lib64:$LD_LIBRARY_PATH"
  CUDA_HOME="/usr/local/cuda"
  export CPATH PATH LD_LIBRARY_PATH CUDA_HOME

  # make conda accessible
  PATH=/opt/conda/envs/pytorch-py3.6/bin:$PATH
  export PATH

%setup
  # runs on host - the path to the image is $SINGULARITY_ROOTFS

%post
  # post-setup script

  # load environment variables
  . /environment

  # make environment file executable
  chmod +x /environment

  # default mount paths, files
  mkdir /scratch /data /work-zfs
  touch /usr/bin/nvidia-smi

  #conda installs (including pytorch)
  /opt/conda/bin/conda install opencv scikit-learn scikit-image scipy pandas
  

  #pip installs 
  /opt/conda/bin/pip install torch torchvision
  /opt/conda/bin/pip install bgen==1.2.6
  /opt/conda/bin/pip install pyro-ppl
  /opt/conda/bin/pip install unidecode
  /opt/conda/bin/pip install statsmodels
  
  

%runscript
  # executes with the singularity run command
  # delete this section to use existing docker ENTRYPOINT command

%test
  # test that script is a success
