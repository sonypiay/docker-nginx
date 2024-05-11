FROM nginx:1.24

ENV NGINX_CONFIG_PATH=/etc/nginx
ENV NGINX_DOCUMENT_ROOT=/var/www/html
ENV TZ="Asia/Jakarta"

RUN ln -snf /usr/share/zoneinfo/${TZ} /etc/localtime && echo ${TZ} > /etc/timezone
RUN apt-get -y update && apt-get -y upgrade
RUN apt-get -y install \
    vim \
    curl
    
RUN apt-get -y autoremove && apt-get -y clean
RUN mkdir -p ${NGINX_DOCUMENT_ROOT}

WORKDIR ${NGINX_CONFIG_PATH}
COPY config/default.conf ${NGINX_CONFIG_PATH}/conf.d/default.conf

WORKDIR ${NGINX_DOCUMENT_ROOT}
COPY src/* ${NGINX_DOCUMENT_ROOT}