FROM tensorflow/tensorflow:2.4.1-gpu-jupyter

RUN apt-get update
RUN apt-get -y install build-essential checkinstall libx11-dev libxext-dev zlib1g-dev libpng-dev libjpeg-dev libfreetype6-dev libxml2-dev
RUN apt-get install -y imagemagick
RUN pip install imageio imageio-ffmpeg configargparse