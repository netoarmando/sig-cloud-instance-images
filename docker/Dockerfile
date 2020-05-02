FROM scratch
ADD CentOS-8-Container-8.1.1911-20200113.3-layer.x86_64.tar.xz  /

LABEL org.label-schema.schema-version="1.0" \
    org.label-schema.name="FreeIPA CentOS Base Image" \
    org.label-schema.vendor="FreeIPA" \
    org.label-schema.license="GPLv2" \
    org.label-schema.build-date="20200303" \
    org.opencontainers.image.title="FreeIPA CentOS Base Image" \
    org.opencontainers.image.vendor="FreeIPA" \
    org.opencontainers.image.licenses="GPL-2.0-only" \
    org.opencontainers.image.created="2020-03-03 15:47:00+02:00"

RUN echo $'[centos-8-stream-devel] \n\
name = CentOS Developmental 8 \n\
baseurl = http://mirror.centos.org/centos/8-stream/Devel/x86_64/os/ \n\
enabled = 1 \n\
gpgcheck = 0 ' > /etc/yum.repos.d/centos-8-stream-devel.repo

RUN echo 'deltarpm = false' >> /etc/dnf/dnf.conf \
    && dnf install -y http://mirror.centos.org/centos/8-stream/BaseOS/x86_64/os/Packages/centos-release-stream-8.1-1.1911.0.7.el8.x86_64.rpm \
    && dnf install -y https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm \
    && dnf update -y dnf \
    && dnf install -y dnf-plugins-core sudo wget \
    && dnf upgrade -y \
    && curl https://download.docker.com/linux/centos/docker-ce.repo -o /etc/yum.repos.d/docker-ce.repo \
    && dnf config-manager --enable PowerTools \
    && dnf clean all

CMD ["/bin/bash"]
