# Docker Image Packaging for GitLab CE

## 13.6.2-XalvistackY - TBC

### Major Changes

## 13.6.2-4alvistack1 - 2020-12-09

### Major Changes

  - Migrate from Travis CI to GitLab CI
  - Rename role as `ansible-role-gitlab_ce`
  - Revamp with Packer

## 13.4.3-4alvistack2 - 2020-10-14

### Major Changes

  - Refine Molecule matrix

## 13.3.1-4alvistack2 - 2020-08-26

### Major Changes

  - Upgrade minimal Ansible Lint support to 4.3.2
  - Upgrade Travis CI test as Ubuntu Focal based
  - Upgrade minimal Ansible support to 2.10.0

## 13.1.4-4alvistack1 - 2020-07-19

  - Ubuntu 20.04 based
  - Minimized `Dockerfile` for meta data definition
  - Provision by Ansible and Molecule Docker driver in single layer
  - Handle `ENTRYPOINT` with [catatonit](https://github.com/openSUSE/catatonit)
