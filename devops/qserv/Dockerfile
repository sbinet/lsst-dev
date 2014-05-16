##
## binet/lsst-qserv
## a Dockerfile to install QServ
##
FROM binet/slc-base

RUN yum install -y \
    antlr \
    boost-devel bzip2 bzip2-devel \
    cmake curl \
    gcc gcc-c++ gettext git glib2-devel glibc-devel \
    java \
    openssl-devel \
    patch \
    perl-ExtUtils-MakeMaker \
    python-devel \
    readline-devel \
    swig \
    ncurses-devel \
    numpy \
    scons \
    tar \
    which \
    zlib-devel

# opt (doc): texlive-latex latex2html

ENV INSTALL_BASE /opt/lsst-sw
ENV BUILDROOT /build/lsst

ENV QSERV_VERSION 6.0.0rc1

RUN mkdir -p ${BUILDROOT} ${INSTALL_BASE}/qserv

## download install script
RUN cd ${BUILDROOT} && \
    curl -O -L http://datasky.in2p3.fr/qserv/distserver/newinstall-qserv-${QSERV_VERSION}.sh && \
    chmod +x newinstall-qserv-${QSERV_VERSION}.sh

## run install script
RUN cd ${BUILDROOT} && \
    ./newinstall-qserv-${QSERV_VERSION}.sh -H $INSTALL_BASE/qserv

## configure qserv
RUN . ${INSTALL_BASE}/qserv/setup-qserv.sh && \
    cd $INSTALL_BASE/qserv/stack/Linux64/qserv/${QSERV_VERSION}/admin && \
    scons || echo "fail"

## clean-up
RUN /bin/rm -rf /build/lsst

CMD ["qserv-start.sh"]
