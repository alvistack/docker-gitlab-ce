# Docker Image Packaging for GitLab

[![Travis](https://img.shields.io/travis/com/alvistack/docker-gitlab.svg)](https://travis-ci.com/alvistack/docker-gitlab)
[![GitHub release](https://img.shields.io/github/release/alvistack/docker-gitlab.svg)](https://github.com/alvistack/docker-gitlab/releases)
[![GitHub license](https://img.shields.io/github/license/alvistack/docker-gitlab.svg)](https://github.com/alvistack/docker-gitlab/blob/master/LICENSE)
[![Docker Pulls](https://img.shields.io/docker/pulls/alvistack/gitlab.svg)](https://hub.docker.com/r/alvistack/gitlab/)

GitLab Software unlocks the power of agile by giving your team the tools to easily create & estimate stories, build a sprint backlog, identify team commitments & velocity, visualize team activity, and report on your team's progress.

Learn more about GitLab: <https://www.atlassian.com/software/gitlab>

## Supported Tags and Respective `Dockerfile` Links

  - [`13.1`, `latest`](https://github.com/alvistack/docker-gitlab/blob/master/molecule/13.1/Dockerfile.j2)

## Overview

This Docker container makes it easy to get an instance of GitLab up and running.

Based on [Official Ubuntu Docker Image](https://hub.docker.com/_/ubuntu/) with some minor hack:

  - Minimized `Dockerfile` for meta data definition
  - Provision by Ansible and Molecule Docker driver in single layer
  - Handle `ENTRYPOINT` with [catatonit](https://github.com/openSUSE/catatonit)

### Quick Start

For the `VOLUME` directory that is used to store the repository data (amongst other things) we recommend mounting a host directory as a [data volume](https://docs.docker.com/engine/tutorials/dockervolumes/#/data-volumes), or via a named volume if using a docker version \>= 1.9.

Start GitLab Server:

    # Pull latest image
    docker pull alvistack/gitlab
    
    # Run as detach
    docker run \
        -itd \
        --privileged \
        --name gitlab \
        --publish 22:22 \
        --publish 80:80 \
        --publish 443:443 \
        --env GITLAB_EXTERNAL_URL=http://localhost/ \
        --volume /var/opt/gitlab:/var/opt/gitlab \
        alvistack/gitlab

**Success**. GitLab is now available on <http://localhost>

## Upgrade

To upgrade to a more recent version of GitLab Server you can simply stop the GitLab
container and start a new one based on a more recent image:

    docker stop gitlab
    docker rm gitlab
    docker run ... (see above)

As your data is stored in the data volume directory on the host, it will still
be available after the upgrade.

Note: Please make sure that you don't accidentally remove the gitlab container and its volumes using the -v option.

## Backup

For evaluations you can use the built-in database that will store its files in the GitLab Server home directory. In that case it is sufficient to create a backup archive of the directory on the host that is used as a volume (`/var/atlassian/application-data/gitlab` in the example above).

## Versioning

### `alvistack/gitlab:latest`

The `latest` tag matches the most recent [GitHub Release](https://github.com/alvistack/docker-gitlab/releases) of this repository. Thus using `alvistack/gitlab:latest` or `alvistack/gitlab` will ensure you are running the most up to date stable version of this image.

### `alvistack/gitlab:<version>`

The version tags are rolling release rebuild by [Travis](https://travis-ci.com/alvistack/docker-gitlab) in weekly basis. Thus using these tags will ensure you are running the latest packages provided by the base image project.

## License

  - Code released under [Apache License 2.0](LICENSE)
  - Docs released under [CC BY 4.0](http://creativecommons.org/licenses/by/4.0/)

## Author Information

  - Wong Hoi Sing Edison
      - <https://twitter.com/hswong3i>
      - <https://github.com/hswong3i>
