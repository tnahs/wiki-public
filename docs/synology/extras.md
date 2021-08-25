# Extras

## Docker

!!! warning "TODO:LOW"

## Plex w/ Docker

!!! note

    Make sure `users` has read/write permissions otherwise Plex won't see media.

    go into the docer terminal and check the permissions

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

```
sudo docker run \
    -p 8000:8000 \
    -p 9000:9000 \
    --detach \
    --name=portainer-ce \
    --restart=always \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v /volume1/docker/portainer-ce:/data portainer/portainer-ce
```

## youtube-dl

<https://www.youtube.com/watch?v=Y-lS-_4mbvc>
<https://nashosted.com/?p=554>

```console
$ docker run -d --name YouTubeDL-Material \
              -v /your/appdata/location:/app/appdata \
              -v /your/audio/location:/app/audio \
              -v /your/video/location:/app/video \
              -v /your/subscriptions/location:/app/subscriptions \
              -v /your/users/location:/app/users \
              -p 8998:17442 \
              tzahi12345/youtubedl-material:latest
```

```
2021-03-28T20:38:05.785Z ERROR: Failed to get config file
```

```
--all-subs,,--sub-format,,srt,,--embed-subs
```

```
%(uploader)s---%(upload_date)s---%(title)s---[%(id)s]
```

<https://github.com/Tzahi12345/YoutubeDL-Material/issues/285>

```json
"custom_args": "--all-subs,,--sub-format,,srt,,--embed-subs",
"custom_output": "%(uploader)s---%(upload_date)s---%(title)s---[%(id)s]"
```

<https://registry.hub.docker.com/r/tzahi12345/youtubedl-material>
