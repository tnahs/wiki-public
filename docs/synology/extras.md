# Extras

## Docker

!!! warning "TODO"

## Plex w/ Docker

!!! note

    Make sure `users` has read/write permissions otherwise Plex won't see media.

    go into the docker terminal and check the permissions

    ```console
    root@plex:/#

    $ ls -la
    ...
    drwxrwx---   1 1026 users  3602 Apr  1 22:47 media-films
    drwxrwx---   1 1026 users    40 Jan 26 22:42 media-music
    ...
    $ cd media-films
    $ ls -la
    ...
    -rwxrwx--- 1 1026 users  2728284260 Apr 17  2018 'The.Ninth.Gate (1999) {imdb-tt0142688}.mp4'
    -rwxrwx--- 1 1026 users  8533360507 May 25  2015 'The.Shawshank.Redemption (1994) {imdb-tt0111161}.mkv'
    ...
    ```

<https://registry.hub.docker.com/r/plexinc/pms-docker/>

<https://en.wikipedia.org/wiki/List_of_tz_database_time_zones>

America/Los_Angeles

ssh admin@192.168.2.20 replacing with your user and IP address of your NAS. Now use ‘id admin’ or whichever user to wish the get the UID and GID for.

It is really important to use the ip of your NAS. I used XXXXX.local to connect to plex server. But then you get no server options. You have to use the real ip. Something like 192.168.1.x:32400/web. <http://ip.addr.of.syno:32400/web> 32.

Do not use XXXX.local. Then you get no server

<https://forums.plex.tv/t/accidentally-deleted-plex-server-from-web-interface/164707>

<https://mariushosting.com/how-to-install-plex-on-your-synology-nas/>

## Portainer

<https://www.wundertech.net/how-to-install-portainer-on-a-synology-nas/>

```console
sudo docker run \
    -p 8000:8000 \
    -p 9000:9000 \
    --detach \
    --name=portainer-ce \
    --restart=always \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v /volume1/docker/portainer-ce:/data portainer/portainer-ce
```
