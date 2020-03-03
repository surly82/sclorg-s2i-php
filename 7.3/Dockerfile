FROM registry.access.redhat.com/ubi8/php-73

USER root

# Update the image with the latest packages (recommended), then
# Install php-xmlrpc module from RHSCL repo, remove override_install_langs so all locales can be installed, install glibc-common for all locales (locale -a)
RUN yum update -y && \
    yum clean all && \
    yum install -y php-xmlrpc && \
    yum install -y glibc-all-langpacks.x86_64  && \
    yum reinstall -y glibc-common && \
    yum clean all

# Might want to refine this (something more specific than $APP_DATA)
RUN chgrp -Rf 0 $APP_DATA && \
    chmod -Rf g+w $APP_DATA && \
    cd $APP_DATA && \
    umask 002

USER 1001
