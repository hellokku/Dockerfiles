FROM debian:buster-slim as builder

# Default Argument values
ARG ARC=amd64
ARG VER=v7.76.1
ARG GCURL_VER=1.8.2
ARG GCURL_ARC=x86_64
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    ca-certificates \
    wget && \
    wget -q https://github.com/moparisthebest/static-curl/releases/download/$VER/curl-$ARC -O /bin/curl && \
    chmod 755 /bin/curl && \
    wget -q https://github.com/fullstorydev/grpcurl/releases/download/v${GCURL_VER}/grpcurl_${GCURL_VER}_linux_${GCURL_ARC}.tar.gz -O - | tar -xz && \
    mv grpcurl /bin/ && \
    chmod 755 /bin/grpcurl


FROM busybox:latest
MAINTAINER kkuroo <kkuroo@nexon.co.kr>
 
# Copy certificates
COPY --from=builder /usr/share/ca-certificates/  /usr/share/ca-certificates/
COPY --from=builder /etc/ssl/ /etc/ssl/
 
# Copy curl
COPY --from=builder /bin/curl  /bin/
COPY --from=builder /bin/grpcurl /bin/

CMD ["/bin/sh"]
