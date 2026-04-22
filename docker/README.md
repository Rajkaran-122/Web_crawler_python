Docker
======

This folder houses the Dockerfiles and settings associated with MetroCrawl.

For more information please check out the [documentation](http://metrocrawl.readthedocs.org)

Want to build your own containers? From the root directory of this project run

```
$ docker build -t <your_tag> -f docker/<component>/Dockerfile .

# build the redis monitor on the dev branch
$ docker build -t digitalmetro/metrocrawl:redis-monitor-dev -f docker/redis-monitor/Dockerfile .
```