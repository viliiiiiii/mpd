FROM debian:stable-slim

RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
      mpd mpc ca-certificates && \
    rm -rf /var/lib/apt/lists/*

# Create needed dirs for MPD runtime files
RUN mkdir -p /var/lib/mpd /playlists

# Copy our config
COPY mpd.conf /etc/mpd.conf

EXPOSE 6600
CMD ["mpd", "--no-daemon", "/etc/mpd.conf"]
