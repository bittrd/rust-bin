FROM rust
WORKDIR /app
VOLUME ["/app"]
RUN rustup target add x86_64-unknown-linux-musl
RUN apt-get update && apt-get install -y musl musl-dev musl-tools
