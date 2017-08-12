FROM tensorflow/tensorflow:latest-gpu

RUN apt-get update && apt-get install -y --no-install-recommends \
         build-essential \
         git \
	 curl \
	 ca-certificates \
	 libjpeg-dev \
	 libpng-dev
	 python3-pip && \
	 rm -rf /var/lib/apt/lists/*
RUN pip install keras

WORKDIR /workspace
RUN chmod -R a+w /workspace
