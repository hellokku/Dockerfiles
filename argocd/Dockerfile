FROM argoproj/argocd:v2.4.11

# Switch to root for the ability to perform install
USER root

# https://askubuntu.com/questions/1420190/upgrade-to-22-04-impish-release-no-longer-has-a-release-file
# Following EOL guide above works, the key is editing the /etc/apt/sources.list so archive.ubuntu.com and security.ubuntu.com are changed to old-releases.ubuntu.com. 
# This allows you to update/upgrade from an EOL version (e.g. Impish). Bette
#RUN sed -i -re 's/([a-z]{2}\.)?archive.ubuntu.com|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list

# Install tools needed for your repo-server to retrieve & decrypt secrets, render manifests 
# (e.g. curl, awscli, gpg, sops)
RUN apt-get update && \
    apt-get install -y wget && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*


RUN wget -qO- https://github.com/helmfile/helmfile/releases/download/v0.145.4/helmfile_0.145.4_linux_amd64.tar.gz | tar xvfz - -C /tmp/ && \
    mv /tmp/helmfile /usr/local/bin/

# Switch back to non-root user
USER 999
