# UW-ESS-DS MLGeo-image JupyterHub Image Builder

This repository builds a [JupyterHub](https://jupyter.org/hub) environment with JupyterHub [GitHub Actions CI](https://github.com/jupyterhub/repo2docker-action)

[![Action Status](https://github.com/UW-ESS-DS/MLGeo-image/workflows/CI/badge.svg)](https://github.com/UW-ESS-DS/MLGeo-image/actions)
[![Docker Pulls](https://img.shields.io/docker/pulls/uwessds/MLGeo-image)](https://hub.docker.com/r/uwessds/MLGeo-image/tags)
[![BinderHub](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/UW-ESS-DS/MLGeo-image/main?urlpath=lab)  

https://hub.docker.com/r/uwessds/mlgeo-image/tags

### How to use:

build with GitHub Actions simply by pushing to GitHub

* pull requests trigger image building without pushing to DockerHub
```
git clone https://github.com/UW-ESS-DS/mlgeo-image
cd MLGeo-image
#git checkout dev
# make sure dev branch is up-to-date with master
git merge master
# modify environment.yml or other files in binder/
git commit -a -m "modified binder/environment to my liking"
git push
# go to github.com and create a pull request to merge dev changes into master
```
* PRs trigger re-building image
* Commits to master build image and push to DockerHub tagged by github commit sha and 'latest'

### Pull your image to run a local JupyterLab session
```
export IMAGE=uwessds/MLGeo-image:latest
export NAME=ESS590
docker run -it --name $NAME -p 8888:8888 $IMAGE jupyter lab --ip 0.0.0.0
docker stop $NAME
docker rm $NAME
```

### Point to a specific tagged image in JupyterHub config
(image: uwessds/mlgeo-image:8192752e54fa)
https://zero-to-jupyterhub.readthedocs.io/en/latest/reference/reference.html?highlight=profile_list#singleuser-profilelist
