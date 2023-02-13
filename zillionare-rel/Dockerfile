# vim:set ft=dockerfile:
#FROM ubuntu:20.04
#WORKDIR /
#COPY rootfs ./
#
#ARG PYPI_INDEX_URL
#ENV DEBIAN_FRONTEND=noninteractive
#
#RUN	apt-get update\
#	&& apt-get -qq install -y --no-install-recommends python3.8 python3-pip build-essential python3.8-dev vim iputils-ping wget #tzdata \ 
#	&& pip3 config set global.index-url $PYPI_INDEX_URL \
#	&& pip3 install $(echo *omega-*.whl) \
#	&& pip3 install --force-reinstall $(echo *adaptors*.whl) \
#	&& pip3 install --force-reinstall $(echo *omicron*.whl) \
#	&& pip3 install -q jupyter jupyter_contrib_nbextensions matplotlib \
#	&& jupyter contrib nbextension install --user >/dev/null \
#	&& rm -rf /var/lib/apt/lists/* \
#	&& rm /*.whl \
#	&& mkdir -p /var/log/zillionare
#
#EXPOSE 3180
#EXPOSE 3181
#EXPOSE 8888
#ENTRYPOINT ["/root/zillionare/entrypoint.sh"]


# vim:set ft=dockerfile:
FROM ubuntu:20.04
WORKDIR /
COPY rootfs ./

ARG PYPI_INDEX_URL
ENV DEBIAN_FRONTEND=noninteractive


RUN	apt-get update\
	&& apt-get install -y --no-install-recommends python3.8 python3-pip build-essential python3.8-dev vim iputils-ping wget tzdata \ 
# && pip3 config set global.index-url https://mirrors.aliyun.com/pypi/simple/ \
 && pip3 config set global.index-url  https://pypi.tuna.tsinghua.edu.cn/simple/ \
	&& pip3 install $(echo *omega-*.whl) \
	&& pip3 install --force-reinstall $(echo *adaptors*.whl) \
	&& pip3 install --force-reinstall $(echo *omicron*.whl) 
RUN pip3 install jupyter jupyter_contrib_nbextensions matplotlib==3.4.1 \
 && pip3 install fqdn isoduration jsonpointer uri-template webcolors numpy==1.20.3\
 && jupyter contrib nbextension install --user >/dev/null \
 && rm -rf /var/lib/apt/lists/* \
 && rm /*.whl \
 && mkdir -p /var/log/zillionare
RUN chmod a+x /root/zillionare/entrypoint.sh

EXPOSE 3180
EXPOSE 3181
EXPOSE 8888
ENTRYPOINT ["/root/zillionare/entrypoint.sh"]
