FROM amazon/aws-cli
MAINTAINER kkuroo <kkuroo@gmail.com>

# Default Argument values
ARG ARC=amd64
ARG GCURL_VER=1.8.2
ARG GCURL_ARC=x86_64

RUN yum install -y iputils bind-utils wget tar zip nc telnet vim && \
    yum clean all && \
    rm -rf /var/cache/yum && \
    wget -q https://github.com/fullstorydev/grpcurl/releases/download/v${GCURL_VER}/grpcurl_${GCURL_VER}_linux_${GCURL_ARC}.tar.gz -O - | tar -xz && \
        mv grpcurl /bin/ && \
        chmod 755 /bin/grpcurl

