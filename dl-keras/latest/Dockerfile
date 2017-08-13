FROM tensorflow/tensorflow:latest-gpu

RUN apt-get update && apt-get install -y --no-install-recommends \
         build-essential \
         git \
	 curl \
	 ca-certificates \
	 libjpeg-dev \
	 libpng-dev \
	 python3-pip && \
	 rm -rf /var/lib/apt/lists/*
RUN cd && git clone http://github.com/fchollet/keras && \
    cd keras && python3 setup.py install && \
    cd .. && rm -rf keras

WORKDIR /workspace
RUN chmod -R a+w /workspace
