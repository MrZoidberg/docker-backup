# http://docs.docker.com/reference/builder
# docker backup via s3 image (boombatower/docker-backup-s3).

FROM boombatower/docker-backup
MAINTAINER Jimmy Berry <jimmy@boombatower.com>

RUN zypper refresh && \
    zypper -n in --no-recommends python-boto python-dateutil python-magic python-xml python-setuptools

ENV S3_CMD_VERSION 1.6.1

ADD https://github.com/s3tools/s3cmd/releases/download/v${S3_CMD_VERSION}/s3cmd-${S3_CMD_VERSION}.tar.gz /root/
RUN cd /root && tar -zxvf s3cmd-${S3_CMD_VERSION}.tar.gz && cd s3cmd-${S3_CMD_VERSION} && python setup.py install

ADD s3.sh /root/bin/

ENTRYPOINT ["/root/bin/s3.sh"]
CMD ["backup"]
