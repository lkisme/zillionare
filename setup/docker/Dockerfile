# vim:set ft=dockerfile:
FROM ubuntu:20.04
WORKDIR /
COPY rootfs ./

ARG PYPI_INDEX_URL
ENV DEBIAN_FRONTEND=noninteractive

RUN	apt-get update

#RUN	apt-get update\
#	&& apt-get -qq install -y --no-install-recommends python3.8 python3-pip build-essential python3.8-dev vim iputils-ping wget tzdata \ 
# && pip3 config set global.index-url $PYPI_INDEX_URL \
# && pip3 install zillionare-omega \
# && pip3 install --force-reinstall zillionare-omega-adaptors-jq==1.0.3 \
# && pip3 install --force-reinstall zillionare-omicron \
# && pip3 install jupyter jupyter_contrib_nbextensions matplotlib \
# && jupyter contrib nbextension install --user >/dev/null \
# && rm -rf /var/lib/apt/lists/* \
# && rm /*.whl \
# && mkdir -p /var/log/zillionare

EXPOSE 3180
EXPOSE 3181
EXPOSE 8888
ENTRYPOINT ["tail"]