# Specify a base image
# Base images should come from a reputable maintainer and should not include unused dependencies
FROM amazoncorretto:11

# Create user and group in order to avoid running the app as root
RUN yum install -y shadow-utils  && \
    groupadd --gid 8899 app1 && \
    useradd --uid 8899 --gid app1 --shell /bin/bash --create-home app1 && \
    yum clean all

CMD "/usr/local/bin/app1"

# Copy the spring boot fat jar from the local file system to the image
COPY target/*exec.jar /usr/local/bin/app1

# make it executable
RUN chmod a+x /usr/local/bin/app1

# Switch to non-root user
USER app1
