# UW ESS Geophysics course ESS314-Fall21-image JupyterHub Image Builder

This repository builds a [JupyterHub](https://jupyter.org/hub) environment with JupyterHub [GitHub Actions CI](https://github.com/jupyterhub/repo2docker-action)

[![Action Status](https://github.com/mdenolle/ESS314-Fall21-image/workflows/CI/badge.svg)](https://github.com/mdenolle/ESS314-Fall21-image/actions)
[![Docker Pulls](https://img.shields.io/docker/pulls/mdenolle/ess314-fall2021-image)](https://hub.docker.com/r/mdenolle/ess314-fall2021-image/tags)
[![BinderHub](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/mdenolle/ess314-fall2021-image/main?urlpath=lab)  

https://hub.docker.com/r/mdenolle/ess314-fall2021-image/tags

### How to use:

build with GitHub Actions simply by pushing to GitHub

* pull requests trigger image building without pushing to DockerHub
```
git clone https://github.com/mdenolle/ESS314-Fall21-image
cd ESS314-Fall21-image
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
export IMAGE=mdenolle/ESS314-Fall21-image:latest
export NAME=ESS590
docker run -it --name $NAME -p 8888:8888 $IMAGE jupyter lab --ip 0.0.0.0
docker stop $NAME
docker rm $NAME
```

### Point to a specific tagged image in JupyterHub config
(image: mdenolle/ess314-fall2021-image:8192752e54fa)
https://zero-to-jupyterhub.readthedocs.io/en/latest/reference/reference.html?highlight=profile_list#singleuser-profilelist
