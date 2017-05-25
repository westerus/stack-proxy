FROM        alpine:latest
MAINTAINER  Westerus <westerus@gmail.com>
LABEL Description="Image with squid service" \
      Version="3.5"

ARG PKG_FLAGS_COMMON="-q"
ARG PKG_FLAGS_PERSISTANT="${PKG_FLAGS_COMMON} --clean-protected --no-cache"
ARG PKG_FLAGS_DEV="${PKG_FLAGS_COMMON} --no-cache"

ARG PKGUPDATE="apk ${PKG_FLAGS_COMMON} update"
ARG PKGUPGRADE="apk ${PKG_FLAGS_PERSISTANT} upgrade"
ARG DELTEMP="rm -rf /var/tmp/* /tmp/*"
ARG PKGINSTALL="apk ${PKG_FLAGS_PERSISTANT} add"

RUN $PKGUPDATE \
  && $PKGUPGRADE \
  && $PKGINSTALL openssl squid \
  && $DELTEMP

ENTRYPOINT ["/entry-point.sh"]
CMD ["squid","-d9","-N"]
