FROM rust
WORKDIR /app
VOLUME ["/app"]
RUN rustup target add x86_64-pc-windows-gnu
RUN apt-get update && apt-get install -y mingw-w64
RUN mkdir -p /.cargo && echo '[target.x86_64-pc-windows-gnu]\n\
linker = "/usr/bin/x86_64-w64-mingw32-gcc"' >> /.cargo/config