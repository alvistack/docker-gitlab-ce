# Docker Image Packaging for GitLab CE

[![Travis](https://img.shields.io/travis/com/alvistack/docker-gitlab-ce.svg)](https://travis-ci.com/alvistack/docker-gitlab-ce)
[![GitHub release](https://img.shields.io/github/release/alvistack/docker-gitlab-ce.svg)](https://github.com/alvistack/docker-gitlab-ce/releases)
[![GitHub license](https://img.shields.io/github/license/alvistack/docker-gitlab-ce.svg)](https://github.com/alvistack/docker-gitlab-ce/blob/master/LICENSE)
[![Docker Pulls](https://img.shields.io/docker/pulls/alvistack/gitlab-ce.svg)](https://hub.docker.com/r/alvistack/gitlab-ce/)

GitLab is a complete DevOps platform, delivered as a single application. This makes GitLab unique and makes Concurrent DevOps possible, unlocking your organization from the constraints of a pieced together toolchain. Join us for a live Q\&A to learn how GitLab can give you unmatched visibility and higher levels of efficiency in a single application across the DevOps lifecycle.

Learn more about GitLab: <https://about.gitlab.com/>

## Supported Tags and Respective Packer Template Links

  - [`13.5`, `latest`](https://github.com/alvistack/docker-gitlab-ce/blob/master/packer/13.5/packer.json)
  - [`13.4`](https://github.com/alvistack/docker-gitlab-ce/blob/master/packer/13.4/packer.json)

## Overview

This Docker container makes it easy to get an instance of GitLab CE up and running.

Based on [Official Ubuntu Docker Image](https://hub.docker.com/_/ubuntu/) with some minor hack:

  - Packaging by Packer Docker builder and Ansible provisioner in single layer
  - Handle `ENTRYPOINT` with [catatonit](https://github.com/openSUSE/catatonit)

### Quick Start

For the `VOLUME` directory that is used to store the repository data (amongst other things) we recommend mounting a host directory as a [data volume](https://docs.docker.com/engine/tutorials/dockervolumes/#/data-volumes), or via a named volume if using a docker version \>= 1.9.

Start GitLab CE Server:

    # Pull latest image
    docker pull alvistack/gitlab-ce
    
    # Run as detach
    docker run \
        -itd \
        --name gitlab-ce \
        --publish 22:22 \
        --publish 80:80 \
        --publish 443:443 \
        --env GITLAB_EXTERNAL_URL=http://localhost/ \
        --volume /var/opt/gitlab:/var/opt/gitlab \
        alvistack/gitlab-ce

**Success**. GitLab CE is now available on <http://localhost>

## Upgrade

To upgrade to a more recent version of GitLab CE Server you can simply stop the GitLab CE
container and start a new one based on a more recent image:

    docker stop gitlab-ce
    docker rm gitlab-ce
    docker run ... (see above)

As your data is stored in the data volume directory on the host, it will still
be available after the upgrade.

Note: Please make sure that you don't accidentally remove the gitlab-ce container and its volumes using the -v option.

## Backup

For evaluations you can use the built-in database that will store its files in the GitLab CE Server home directory. In that case it is sufficient to create a backup archive of the directory on the host that is used as a volume (`/var/opt/gitlab` in the example above).

## Versioning

### `alvistack/gitlab-ce:latest`

The `latest` tag matches the most recent [GitHub Release](https://github.com/alvistack/docker-gitlab-ce/releases) of this repository. Thus using `alvistack/gitlab-ce:latest` or `alvistack/gitlab-ce` will ensure you are running the most up to date stable version of this image.

### `alvistack/gitlab-ce:<version>`

The version tags are rolling release rebuild by [Travis](https://travis-ci.com/alvistack/docker-gitlab-ce) in weekly basis. Thus using these tags will ensure you are running the latest packages provided by the base image project.

## License

  - Code released under [Apache License 2.0](LICENSE)
  - Docs released under [CC BY 4.0](http://creativecommons.org/licenses/by/4.0/)

## Author Information

  - Wong Hoi Sing Edison
      - <https://twitter.com/hswong3i>
      - <https://github.com/hswong3i>
