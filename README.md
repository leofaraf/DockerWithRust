<div align="center">
<img src="rust-is-revolution.png" alt="drawing" width="350"/>

# Hello, it will be step-by-step guide how to create simple docker image with Rust
</div>

It was my first experience with `docker`+`rust`, 
but I have decided that I must share it :)

## Steps to done it:

### Requirements
- install `docker` for your machine
- install `rust` image in your docker, like `docker pull rust:1.73.0`

### Prepare rust project
You can just download this project and continue on the next part, OR

#### Create your hello-world project
- `cargo init`
- write `[your_project_name]` in `name` property  in `Cargo.toml`
- create `Dockerfile` in index-dir of your project
- write in this file like this template:

```
# This tells docker to use the Rust official image
FROM rust:1.73.0

# Copy the files in your machine to the Docker image
COPY ./ ./

# Build your program for release
RUN cargo build --release

# Run the binary
CMD ["./target/release/[your_project_name]"]
```

### Compile docker image
`docker build -t rust-hello-world`

### Great. You have done it. Just write one command:
`docker run rust-hello-world`
