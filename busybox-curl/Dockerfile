FROM debian:buster-slim as builder

# Default Argument values
ARG ARC=amd64
ARG VER=v7.76.1

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    ca-certificates \
    wget && \
    wget -q https://github.com/moparisthebest/static-curl/releases/download/$VER/curl-$ARC -O /bin/curl && \
    chmod 755 /bin/curl


FROM busybox:latest
MAINTAINER Dennis.Koo <kkuroo@gmail.com>

# Copy certificates
COPY --from=builder /usr/share/ca-certificates/  /usr/share/ca-certificates/
COPY --from=builder /etc/ssl/ /etc/ssl/

# Copy certificates
COPY --from=builder /bin/curl  /bin/

CMD ["/bin/sh"]
