FROM debian:stable-slim

RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
      mpd mpc libshout3 dumb-init netcat-openbsd \
 && rm -rf /var/lib/apt/lists/*

# folders MPD needs
RUN mkdir -p /var/lib/mpd /playlists

# MPD runs as root in the container so volumes are always writable
COPY mpd.conf /etc/mpd.conf

EXPOSE 6600
ENTRYPOINT ["/usr/bin/dumb-init", "--"]
CMD ["mpd", "--no-daemon", "--stdout", "/etc/mpd.conf"]
