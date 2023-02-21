# vim:set ft=dockerfile:
FROM ubuntu:20.04
WORKDIR /
COPY rootfs ./

ARG PYPI_INDEX_URL
ENV DEBIAN_FRONTEND=noninteractive

RUN	apt-get update\
	&& apt-get install -y --no-install-recommends python3.8 python3-pip build-essential python3.8-dev vim iputils-ping wget tzdata \ 
	&& pip3 config set global.index-url $PYPI_INDEX_URL 
RUN pip install jqdatasdk
RUN apt-get -y install git cmake
RUN mkdir /workspace && cd /workspace \
 	&& git clone https://github.com/libfann/fann.git \
	&& cd /workspace/fann \
	&& cmake -DCMAKE_INSTALL_PREFIX=/workspace/libfann . \
	&& make install \
	&& export LD_LIBRARY_PATH=/workspace/libfann/lib/



#EXPOSE 3180
#EXPOSE 3181
#EXPOSE 8888
ENTRYPOINT ["tail"]
