# Docker Pandoc Builder

![Build Status](https://github.com/maxkratz/docker_pandoc-builder/actions/workflows/build-and-push.yml/badge.svg?branch=main)

*Unofficial* [Pandoc](https://github.com/jgm/pandoc) Dockerfile.
Prebuild images can be found at this [Dockerhub repository](https://hub.docker.com/r/maxkratz/pandoc-builder).

*Unofficial* [TeX Live](https://www.tug.org/texlive/) Dockerfile for various versions.
Prebuild images can be found at this [Dockerhub repository](https://hub.docker.com/r/maxkratz/texlive).


## Quickstart
After installing [Docker](https://docs.docker.com/get-docker/), just run the following command inside your LaTeX workspace.
It will mount the current directory to `/data` inside the container.
This path will be used as working directory as defined in the Dockerfile.

```sh
docker run --rm -it -v $PWD:/data maxkratz/pandoc-builder:latest pandoc input.md -o output.pdf --from markdown --template eisvogel
```

If you have a Makefile defined just run the following command from your workspace:

```sh
docker run --rm -it -v ${PWD}:/data maxkratz/pandoc-builder:latest make
```


## Dockerfile
The [Dockerfile](https://github.com/maxkratz/docker_pandoc-builder/blob/main/Dockerfile) can be found at the GitHub repository.


## What gets installed in this image?
The following packages are installed in this Docker image:

* Some utility packages like wget and build essentials etc.
* [TeX Live](https://www.tug.org/texlive/acquire-netinstall.html)
* [Pandoc](https://github.com/jgm/pandoc)
* [Eisvogel template](https://github.com/Wandmalfarbe/pandoc-latex-template)


## Issues & Contribution
If you find any problems, bugs or missing packages, feel free to open an [issue on Github](https://github.com/maxkratz/docker_pandoc-builder/issues).


## Runner requirements
Currently, all actions must be run by a self-hosted GitHub runner, because GitHub-hosted runners do not have enough storage available.

### Self-hosted Linux-based runners
In order to run the "GitHub Actions" pipeline on a self-hosted runner, you must ensure that you have at least one properly configured Linux-based runner added to this GitHub project.

Required packages (at least):
- `curl`
- `wget`
- `grep`
- `docker` (including buildx plugin)
