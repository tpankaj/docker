FROM nvidia/cuda

COPY ./keyboard /etc/default/keyboard

RUN apt-get update && apt-get install -y --no-install-recommends \
         build-essential \
         git \
	 curl \
	 ca-certificates \
	 libjpeg-dev \
	 xserver-xorg \
	 libpng-dev && \
	 rm -rf /var/lib/apt/lists/*

RUN curl -o ~/miniconda.sh -O https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh  && \
     chmod +x ~/miniconda.sh && \
     ~/miniconda.sh -b -p /opt/conda && \
     rm ~/miniconda.sh
ENV PATH /opt/conda/bin:$PATH
RUN conda install -q numpy pyyaml scipy matplotlib ipython mkl h5py pyserial termcolor opencv pandas
RUN conda install -q -c soumith magma-cuda80
RUN conda install -q pytorch torchvision cuda80 -c soumith

WORKDIR /workspace
RUN chmod -R a+w /workspace
