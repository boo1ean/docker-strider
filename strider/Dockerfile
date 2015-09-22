FROM ubuntu:14.04
MAINTAINER Egor Gumenyuk <boo1ean0807@gmail.com>

ENV STRIDER_TAG v1.7.3
ENV STRIDER_REPO https://github.com/Strider-CD/strider

RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8  
ENV LANGUAGE en_US:en  
ENV LC_ALL en_US.UTF-8  

RUN apt-get update && \
	apt-get install -y git nodejs npm && \
	update-alternatives --install /usr/bin/node node /usr/bin/nodejs 10 && \
	npm install -g pm2

RUN mkdir -p /home/strider && mkdir -p /opt/strider
RUN adduser --disabled-password --gecos "" --home /home/strider strider
RUN chown -R strider:strider /home/strider

USER strider
ENV HOME /home/strider

# Clone and build strider

RUN git clone --branch $STRIDER_TAG --depth 1 $STRIDER_REPO /home/strider/src && \
	cd /home/strider/src && npm install && npm run build

EXPOSE 3000
USER root

COPY start-service.sh /home/strider/start-service.sh

CMD ["bash", "/home/strider/start-service.sh"]
