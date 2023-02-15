# vim:set ft=dockerfile:
FROM ubuntu:20.04
WORKDIR /
COPY rootfs ./

ARG PYPI_INDEX_URL
ENV DEBIAN_FRONTEND=noninteractive

RUN	apt-get update\
	&& apt-get install -y --no-install-recommends python3.8 python3-pip build-essential python3.8-dev vim iputils-ping wget tzdata 

RUN pip3 config set global.index-url $PYPI_INDEX_URL \
	&& pip3 install $(echo *omega-*.whl) \
	&& pip3 install https://github.com/lkisme/omega_jqadaptor/releases/download/v1.0.3-alpha/zillionare_omega_adaptors_jq-1.0.3a0-py3-none-any.whl \
	&& pip3 install --force-reinstall $(echo *omicron*.whl) \
	&& pip3 install -q jupyter jupyter_contrib_nbextensions matplotlib==3.4.1 \
    && pip3 install fqdn isoduration jsonpointer uri-template webcolors pyecharts \
	&& jupyter contrib nbextension install --user >/dev/null \
	&& rm -rf /var/lib/apt/lists/* \
	&& rm /*.whl \
	&& mkdir -p /var/log/zillionare
RUN pip3 install jqdatasdk -U
RUN chmod a+x /root/zillionare/entrypoint.sh
#解决numpy和pandas的问题
#RUN pip install jqdatasdk -U 

EXPOSE 3180
EXPOSE 3181
EXPOSE 8888
ENTRYPOINT ["/root/zillionare/entrypoint.sh"]



#pip install zillionare-omega==1.1.0.1
#pip install zillionare-omega-adaptors-jq
#pip install zillionare-omicron==1.1.1
#
#
#pip show zillionare-omega-adaptors-jq
#pip install zillionare-omega-adaptors-jq
#pip install jqdatasdk
#
#pip3 install --force-reinstall jqdatasdk==1.8.9
#Successfully installed SQLAlchemy-2.0.3 certifi-2022.12.7 charset-normalizer-3.0.1 greenlet-2.0.2 idna-3.4 jqdatasdk-1.8.9 msgpack-1.0.4 numpy-1.24.2 pandas-1.5.3 ply-3.11 pymysql-1.0.2 #python-dateutil-2.8.2 pytz-2022.7.1 requests-2.28.2 six-1.16.0 thriftpy2-0.4.16 typing-extensions-4.4.0 urllib3-1.26.14
#tail -f /var/log/zillionare/omega.log
#
#pip3 install SQLAlchemy==1.3.24