# VM Hub [![Build Status](https://api.travis-ci.org/alex-agency/vmhub.png)](https://travis-ci.org/alex-agency/vmhub)

Version Manager Docker Hub


To build image using boot2docker:

Copy the sources to following path:
MacOS: /Users/<USERNAME>/Docker/vmhub 
Windows: /c/Users/<USERNAME>/Docker/vmhub

```
# docker build --force-rm=true -t alexagency/vmhub /Users/Alex/Docker/vmhub
```

To run container in the background:

```
# docker run -d -p 80:80 -p 9019:9019 -p 8000:8000 \
 -v /var/run/docker.sock:/var/run/docker.sock alexagency/vmhub
or
# fig up -d
```

To run interactive with remove container after exit (--rm):

```
# docker run -it --rm -p 80:80 -p 9019:9019 -p 8000:8000 \
 -v /var/run/docker.sock:/var/run/docker.sock alexagency/vmhub
or
# fig up
```

To run Fig via container:

```
# alias fig='docker run --rm -it \
        -v $(pwd):/app \
        -v /var/run/docker.sock:/var/run/docker.sock \
        -e FIG_PROJECT_NAME=$(basename $(pwd)) \
        dduportal/fig'
# fig
```

NodeJS server:

```
# http://<DOCKERHOST>:8080/
```

Karma Test Runner:

```
# browsers: Firefox, Chrome
# link: http://<DOCKERHOST>:9019/
```

To run interactive container with continuous update source code ($PWD/src) on the fly:

```
# docker run -it --rm -p 80:80 -p 9019:9019 -p 8000:8000 \
 -v /var/run/docker.sock:/var/run/docker.sock -v $PWD/src:/usr/src/src alexagency/vmhub
```

To remove all stoped containers:

```
# docker rm $(docker ps -a -q)
```
