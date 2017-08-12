FROM nvidia/cuda

LABEL com.nvidia.volumes.needed="nvidia_driver"
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
RUN conda install numpy pyyaml mkl setuptools cmake gcc cffi
RUN conda install -c soumith magma-cuda80
RUN conda clean -ya
RUN cd && \
    git clone https://github.com/pytorch/pytorch && \
    cd pytorch && \
    python setup.py install && \
    cd .. && rm -rf pytorch

ENV LD_LIBRARY_PATH /usr/local/nvidia/lib:/usr/local/nvidia/lib64

WORKDIR /workspace
RUN chmod -R a+w /workspace
