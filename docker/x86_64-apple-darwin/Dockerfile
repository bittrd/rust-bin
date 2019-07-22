FROM rust
WORKDIR /app
VOLUME ["/app"]
RUN rustup target add x86_64-apple-darwin
RUN apt-get update && apt-get install -y clang cmake
RUN cd ~ \
    && git clone https://github.com/tpoechtrager/osxcross \
    && cd osxcross \
    && wget -nc https://s3.dockerproject.org/darwin/v2/MacOSX10.10.sdk.tar.xz \
    && mv MacOSX10.10.sdk.tar.xz tarballs/ \
    && UNATTENDED=yes OSX_VERSION_MIN=10.7 ./build.sh
ENV PATH /root/osxcross/target/bin:${PATH}
RUN mkdir -p /.cargo && echo '[target.x86_64-apple-darwin]\n\
linker = "x86_64-apple-darwin14-clang"\n\
ar = "x86_64-apple-darwin14-ar"' >> /.cargo/config
RUN apt-get update && apt-get install -y \
    clang \
    gcc \
    g++ \
    zlib1g-dev \
    libmpc-dev \
    libmpfr-dev \
    libgmp-dev
ENV CC o64-clang
ENV CXX o64-clang++