FROM binet/slc-dev

RUN yum install -y \
    antlr \
    boost-devel bzip2 bzip2-devel \
    cmake \
    gcc gcc-c++ gettext git glib2-devel glibc-devel \
    java \
    openssl-devel \
    patch \
    perl-ExtUtils-MakeMaker \
    python-devel \
    readline-devel \
    swig \
    numpy \
    scons \
    zlib-devel

# opt (doc): texlive-latex latex2html

RUN mkdir -p /build/lsst /opt/qserv-dev

RUN git clone git://dev.lsstcorp.org/LSST/DMS/qserv \
    -b tickets/3100 \
    /build/lsst/qserv

ENV QSERV_SRC_DIR /build/lsst/qserv
RUN export QSERV_SRC_DIR=/build/lsst/qserv
RUN cd ${QSERV_SRC_DIR} && /bin/sh ./eupspkg/newinstall-qserv.sh -H /opt/qserv-dev

## clean-up
RUN /bin/rm -rf /build/lsst
