![dbt-logo](https://imgur.com/rGpbwpH.png)

# DBT

[Docker](https://www.docker.com/what-docker) image for [DBT-labs (former FishtownAnalytics) data build tool (DBT)](https://www.getdbt.com/product/).

![Docker Cloud Automated build](https://img.shields.io/docker/cloud/automated/article1dataops/dbt) ![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/article1dataops/dbt) ![Docker Pulls](https://img.shields.io/docker/pulls/article1dataops/dbt)

## Important notice
Since version 1.0.0 my images are optimized for two different architectures: **AMD 64** and **ARM 64**. Last one is really helpful for running on [Apple M1](https://en.wikipedia.org/wiki/Apple_M1) machines.


## Full
- ![Docker Image Version (tag latest semver)](https://img.shields.io/docker/v/article1dataops/dbt/latest?color=brightgreen) ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/article1dataops/dbt/latest?color=brightgreen)

- ![dbt 1.6 FULL](https://img.shields.io/docker/v/article1dataops/dbt/1.6?color=brightgreen) ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/article1dataops/dbt/1.6?color=brightgreen)   __= 1.6.0__

- ![dbt 1.5 FULL](https://img.shields.io/docker/v/article1dataops/dbt/1.5?color=brightgreen) ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/article1dataops/dbt/1.5?color=brightgreen)   __= 1.5.4__

- ![dbt 1.4 FULL](https://img.shields.io/docker/v/article1dataops/dbt/1.4?color=brightgreen) ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/article1dataops/dbt/1.4?color=brightgreen)   __= 1.4.5__

- ![dbt 1.3 FULL](https://img.shields.io/docker/v/article1dataops/dbt/1.3?color=brightgreen) ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/article1dataops/dbt/1.3?color=brightgreen)   __= 1.3.2__

- ![dbt 1.2 FULL](https://img.shields.io/docker/v/article1dataops/dbt/1.2?color=yellowgreen) ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/article1dataops/dbt/1.2?color=yellowgreen)   __= 1.2.5__

- ![dbt 1.1 FULL](https://img.shields.io/docker/v/article1dataops/dbt/1.1?color=yellow) ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/article1dataops/dbt/1.1?color=yellow)   __= 1.1.4__

- ![dbt 1.0 FULL](https://img.shields.io/docker/v/article1dataops/dbt/1.0?color=orange) ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/article1dataops/dbt/1.0?color=orange)    __= 1.0.8__

## BigQuery Spins

- ![BigQuery Spin 1.6](https://img.shields.io/docker/v/article1dataops/dbt-bigquery/1.6?label=BigQuery&color=blue) ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/article1dataops/dbt-bigquery/1.6)

- ![BigQuery Spin 1.5](https://img.shields.io/docker/v/article1dataops/dbt-bigquery/1.5?label=BigQuery&color=blue) ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/article1dataops/dbt-bigquery/1.5)

- ![BigQuery Spin 1.4](https://img.shields.io/docker/v/article1dataops/dbt-bigquery/1.4?label=BigQuery&color=blue) ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/article1dataops/dbt-bigquery/1.4)


More images you can find on [tags page](https://hub.docker.com/r/article1dataops/dbt/tags?ordering=last_updated)


# Overview
The main idea is to give possibility to work with DBT without unnesessary components and via Docker way.

The image is more tiny than official one but provides the same functionality.

# What is DBT?

dbt is a development environment that speaks the preferred language of data analysts everywhere—SQL. With dbt, analysts take ownership of the entire analytics engineering workflow, from writing data transformation code to deployment and documentation.

![dbt diadram](https://user-images.githubusercontent.com/1247388/227546451-e643cfe3-b22d-46f8-a1f1-668a35b4c633.JPG)

## Official documentation and guides

All official documentation can be found on [DBT Docs](https://docs.getdbt.com/)

# How to build with particular version and/or plugins set

You can build the image with desired plugins set and/or DBT version.

`docker build -t <YOUR_TAG>  --build-arg VERSION=<DESIRED_VERSION> --build-arg PLUGINS='bigquery redshift, snowflake' <YOUR_DOCKER_FILE>`

### Image building examples

- `docker build -t myorg/dbt:bigquery --build-arg PLUGINS=bigquery .`

- `docker build -t myorg/dbt:0.21 --build-arg VERSION='0.21.1' --build-arg PLUGINS='bigquery snowflake,redshift' .`

- `Get-Content Dockerfile-1.0 | docker build -t myorg/dbt:1.0 --build-arg VERSION='1.0.9' --build-arg PLUGINS='bigquery,snowflake,redshift' -`

Just grab Dockerfile and build desired version and/or plugins list as build parametes.
If no parameters will be passed into the build then image will be built using latest release version from [this page](https://github.com/dbt-labs/dbt-core/releases/latest) and following components:
- DBT version before 1.0.0 - DBT core + BigQuery + Snowflake + Redshift + Postgres
- DBT version 1.0.0 and  after - DBT core only


Version list can be found on [DBT-labs GitHub](https://github.com/dbt-labs/dbt-core/tags) repo.

Plugins list can be found in [DBT documentation](https://docs.getdbt.com/docs/available-adapters) site.
Please use plugin name from **Install from PyPi** section (without `dbt-` prefix) to pass it as a build argument

## Important notice
To avoid auto-downgrading of DBT-core version during outdated plugin installation, I've added strict condition that plugin's version must be equal to version of DBT-core.

You need to edit the Dockerfile if you need to create your own 1.0 and 1.3 images as they are specifics to these minor versions.

# This is a Fork !!

**This project is a fork of xemulian dbt repository.**

We have decided to fork and maintain our own images because [he ignored our help](https://github.com/xemuliam/docker-dbt/issues/6#issuecomment-1431428762) to maintain and publish new images and we needed to stay up-to-date with the official dbt project.
