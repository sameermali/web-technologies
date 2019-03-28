# use base image
FROM ubuntu:18.04

# run linux commands
RUN mkdir /apps
RUN chmod 2755 /apps

# copy from host to image
COPY target/foo.jar /apps/foo/current

# if kicking java app by executing shell script, container will once shell script execution is completed
# so insert sleep infinity
ENTRYPOINT /bootstrap.sh; sleep infinity