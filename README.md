# Rust Microservice Reference Document

## Pre-requisites

Install Docker: https://docs.docker.com/install/
(For some examples)
Install Rust and Cargo: https://www.rust-lang.org/tools/install

## 01-hello-world
Before we build a microservice, we must first containerize! 

### Simple Hello World (non-Docker)
In this directory you'll find a file in `src/` called `main.rs` 

To run without docker, run `cargo build --release` and then `./target/release/hello-world` 
Now we will containerize and run the exact same sets of commands inside of a container 

### Simple Hello World (with Docker)

In the `01-hello-world` directory to build:
`docker build -t hello-world-rust .` 
and then to run: 
`docker run -it hello-world-rust`

## 01-hello-web-server
//TODO
