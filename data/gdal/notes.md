Find the right docker image.
https://hub.docker.com/r/jupyter/base-notebook

Let's run the Jupyter with the container and mount our direcotry with the notebook
```sh
docker run -v $PWD:/home/jovyan/work -p 8888:8888 jupyter/base-notebook
```
There is one new element here:
-p option allows us to map the ports
Jupyter notebook server is accessed bia 8888 port. We are going to map 8888 port in the container to 8888 port on our (host) computer.

When we try to run the notebook, we see we don't have the gdal libraries available.

Let's try to install the dependecies inside the container. To do it, we are going to run the container in the interactive mode. We do need to install new packages and we will need root access.

```sh
docker run -it -e GRANT_SUDO=yes --user root jupyter/base-notebook /bin/bash
```

We are going to install python libraries gdal and matplotlib, which we use in this our notebook.

```sh
conda install gdal
conda install matplotlib
```

It worked in the container, lets put it not in the Docekrfile and try to build an image

`Dckerfile`
```
FROM jupyter/base-notebook

RUN conda install gdal
Run conda install matplotlib
```

Let's build the container and name it jupyter-gdal.
```sh
docker build -t jupyter-gdal .
```

Let's run it. Dont' forget to mount our folder with data we want to visualise
```sh
docker run -v $PWD:/home/jovyan/work -p 8888:8888 jupyter-gdal
```
