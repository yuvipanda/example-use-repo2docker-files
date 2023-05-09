# Inherit from a community maintained image

This repo is an example of using [repo2docker-action](https://github.com/jupyterhub/repo2docker-action)
to build a user image for your JupyterHub using [files supported by repo2docker](https://repo2docker.readthedocs.io/en/latest/config_files.html).

## Features

1. Use an `environment.yml` to fully specify the packages we want. This file is not specific to containers, and
   regular users can use it too!
2. Use an `apt.txt` file to specify packages to install from apt.
3. Users can test out their image **interactively** by making a PR, which will automatically create a comment with a link to
   mybinder.org, which will build the image *exactly* the same way our action does. This allows users to contribute packages
   and changes to this repo without needing docker installed locally. [See example PR](https://github.com/yuvipanda/example-inherit-from-community-image/pull/1)
4. On making PRs, a GitHub action builds the image to make sure it can be built. This catches issues with syntax errors and
   missing versions.
5. Tests inside the `image-tests/` directory are also run on each PR, allowing for more fine-grained tests - either as
   `pytest` tests or as jupyter notebooks that must reproduce exactly. This helps catch issues with version upgrades breaking
   your instructional code.
6. When a PR is merged, the image is built and pushed to [quay.io](https://quay.io/repository/yuvipanda/example-inherit-from-community-image?tab=info)
