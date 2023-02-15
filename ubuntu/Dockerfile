# vim:set ft=dockerfile:
FROM ubuntu:20.04
WORKDIR /
COPY rootfs ./

ARG PYPI_INDEX_URL
ENV DEBIAN_FRONTEND=noninteractive

RUN	apt-get update\
	&& apt-get -qq install -y --no-install-recommends python3.8 python3-pip build-essential python3.8-dev vim iputils-ping wget tzdata \ 
	&& pip3 config set global.index-url $PYPI_INDEX_URL 
RUN pip install jqdatasdk

#RUN pip3 install numpy==1.20.3
#RUN chmod a+x /root/zillionare/entrypoint.sh
#解决numpy和pandas的问题
#RUN pip install jqdatasdk -U 

EXPOSE 3180
EXPOSE 3181
EXPOSE 8888
ENTRYPOINT ["tail"]
