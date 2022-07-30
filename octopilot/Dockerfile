FROM debian:buster-slim as builder

# Default Argument values
ARG ARC=amd64
ARG CURL_VER=v7.76.1
ARG OTP_VER=1.0.22

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    ca-certificates \
    wget && \
    wget -q https://github.com/moparisthebest/static-curl/releases/download/$CURL_VER/curl-$ARC -O /bin/curl && \
    chmod 755 /bin/curl && \
    wget -q https://github.com/dailymotion-oss/octopilot/releases/download/v$OTP_VER/octopilot_${OTP_VER}_linux_${ARC} -O /bin/octopilot && \
    chmod 755 /bin/octopilot

FROM busybox:latest
MAINTAINER Dennis.Koo <kkuroo@gmail.com>

# Copy certificates
COPY --from=builder /usr/share/ca-certificates/  /usr/share/ca-certificates/
COPY --from=builder /etc/ssl/ /etc/ssl/

# Copy binary
COPY --from=builder /bin/curl  /bin/
COPY --from=builder /bin/octopilot  /bin/

CMD ["/bin/sh"]
