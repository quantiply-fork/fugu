fugu
====

## What is fugu?

 * fugu is a ``docker run`` wrapper
 * fugu loads ``run`` arguments from a fugu.yml file and 
   merges these arguments with command line arguments
 * Usage: ``fugu <command> [fugufile] [label] [docker-options]``
 * fugu is NOT an orchestration tool like [fig](https://github.com/docker/fig). 

 
Example ``fugu.yml``

```yml
image:  mattes/hello-world-nginx # mandatory
name:   hello-world-nginx
detach: true
publish:
  - 8080:80
```

Multiple configurations are supported per fugu.yml with labels. See [advanced fugu.yml](fugu.example.yml)).

# Installation

```bash
go get github.com/mattes/fugu

# TODO: release pre-compiled versions
```

## Why fugu?

We are working on [developermail.io](https://developermail.io) atm. 
The project uses a microservice architecture and consists of >15 docker images. 
During development a docker container is built, run and destroyed quite often.
With fugu we can speed up this workflow, because all ``docker run`` arguments
are stored in the ``fugu.yml`` file. We also used to put ``docker run`` statements 
in ``README.md``, but the format wasn't consistent. Now ``fugu.yml`` is our second point of contact 
(after the Dockerfile itself), when looking at a new docker image. 
We didn't want to use fig, because the set of containers we run during
development changes often and we didn't want to keep one ``fig.yml`` for every
possible docker container combination.


---

[![Build Status](https://travis-ci.org/mattes/fugu.svg?branch=master)](https://travis-ci.org/mattes/fugu)
[![GoDoc](https://godoc.org/github.com/mattes/fugu?status.svg)](https://godoc.org/github.com/mattes/fugu)

