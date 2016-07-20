# Docker files to create Docker images with deal.II  

[![Build Status](https://travis-ci.org/dealii/docker-files.svg?branch=master)](https://travis-ci.org/dealii/docker-files)

Started from @tjhei, edited by @luca-heltai

To each directory in this repository, one (or more) images are built either on dockerhub, or on travis. 

In particular

- ubuntu14
- base

contain the startup OS and a minimal set of packages to compile serial builds. Both images are built
on dockerhub:

- https://hub.docker.com/r/dealii/ubuntu14/
- https://hub.docker.com/r/dealii/base/

The directory full-deps contain docker images to download and install all external dependencies
for deal.II, using two possible different methods:

- candi
- manual

The building of these images is very expensive, and it is done manually, when important updates
are available on the external libraries.

The directory dealii, finally, contains the Dockerfiles to build the actual deal.II library images, 
in particular we build several different types of deal.II images, each on its own tag. Tags are named
based on the type of base system that is used to bootstrap the build:

- bare
- candi
- manual

And for each of these, build types *Debug*, *Release*, or *DebugRelease* are built, with the final
images stored in

- bare-debug
- bare-debug-release
- bare-release
- candi-debug
- ...

You can pull any of the above image from dockerhub using (for example)

    docker pull dealii/dealii:candi-debug

and you can run an interactive shell in it:

    docker run -i -t dealii/dealii:candi-debug

This will drop you in an isolated environment where you can experiment with deal.II. 
