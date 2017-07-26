FROM ubuntu:xenial

RUN apt-get update \
  && apt-get install -y --no-install-recommends \
    liblua5.3-0 \
    libpcre3 \
    libssl1.0.0 \
    haproxy \
  && rm -rf /var/lib/apt/lists/* \
  && apt-get purge -y

COPY docker-entrypoint.sh /
RUN chmod 755 /docker-entrypoint.sh
RUN mkdir -p /run/haproxy/ /var/run/haproxy/
ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["haproxy", "-f", "/etc/haproxy/haproxy.cfg"]
