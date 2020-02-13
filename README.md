# Rust Microservice Reference Document

## Pre-requisites

Install Docker: https://docs.docker.com/install/
(For some examples)
Install Rust and Cargo: https://www.rust-lang.org/tools/install

## 01-hello-world
Before we build a microservice, we must first containerize! 

### Simple Hello World (non-Docker)
In this directory you'll find a file in `src/` called `main.rs` 

To run without docker, build:  
`cargo build --release` and run:  
`./target/release/hello-world` 

Now we will containerize and run the exact same sets of commands inside of a container  

### Simple Hello World (with Docker)

In the `01-hello-world` directory to build:  
`docker build -t hello-world-rust .`  
and then to run:  
`docker run -it hello-world-rust`  

## 02-hello-world-distroless

Distroless is a safe and lightweight way to run your container images, to do this we will use the following Dockerfile (also in `02-hello-world-distroless`: 
```
FROM rust:1.41.0 as build-env
WORKDIR /app
ADD . /app
RUN cargo build --release

FROM gcr.io/distroless/cc
COPY --from=build-env /app/target/release/hello-world-distroless /
CMD ["./hello-world-distroless"]
```

Here we can see the first stage runs up until `cargo build --release`, after that we grab the `distroless/cc` image which is the base image of distroless plus libgcc1 and its dependencies and add the `/target/release` directory.  From there we run the new binary.  
The same commands above will help us build and run this image: 
Build: 
`docker build -t hello-world-rust-distroless .` 
Run: 
`docker run -it hello-world-rust` 
