FROM nvidia/cuda

RUN apt-get update && apt-get install -y --no-install-recommends \
         build-essential \
         git \
	 curl \
	 ca-certificates \
	 libjpeg-dev \
	 libpng-dev && \
	 rm -rf /var/lib/apt/lists/*

RUN curl -o ~/miniconda.sh -O https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh  && \
     chmod +x ~/miniconda.sh && \
     ~/miniconda.sh -b -p /opt/conda && \
     rm ~/miniconda.sh
ENV PATH /opt/conda/bin:$PATH
ENV CMAKE_PREFIX_PATH /opt/conda/
RUN conda install numpy pyyaml scipy ipython mkl
RUN conda install -c soumith magma-cuda80
RUN conda install pytorch torchvision cuda80 -c soumith

WORKDIR /workspace
RUN chmod -R a+w /workspace
