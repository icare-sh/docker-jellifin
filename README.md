# docker-jellifin

docker run -d\
  --name=sonarr \
  -e PUID=1000 \
  -e PGID=1000 \
  -e TZ=Europe/Paris \
  -p 8989:8989 \
  -v /root/docker/tv:/tv \
  -v /root/docker/downloads:/downloads \
  --restart unless-stopped \
  linuxserver/sonarr

docker run -d \
 --name=radarr \
  -e PUID=1000 \
  -e PGID=1000 \
  -e TZ=Europe/Paris \
  -p 7878:7878 \
  -v /root/docker/movies:/movies \
  -v /root/docker/downloads:/downloads \
  --restart unless-stopped \
  linuxserver/radarr

docker run -d \
  --name=jellyfin \
  -e PUID=1000 \
  -e PGID=1000 \
  -e TZ=Europe/Paris \
  -p 8096:8096 \
  -v /root/docker/tv:/data/tvshows \
  -v /root/docker/movies:/data/movies \
  --restart unless-stopped \
  ghcr.io/linuxserver/jellyfin

docker run -d \
--name=portainer \
-p 8000:8000 \
-p 9000:9000 \
--restart=always \
-v /var/run/docker.sock:/var/run/docker.sock \
-v portainer_data:/data \
portainer/portainer-ce