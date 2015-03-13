#kierranm/plex
<i>This is a docker image setup to run <a href="http://plex.tv/">plex media server</a></i>

The image includes mount points for the following directories, that you will need to configure:
 * ```/tv``` -> TV Library
 * ```/movies``` -> Movies Library
 * ```/music``` -> Music Library
 * ```/photos``` -> Photos Library
 * ```/videos``` -> Home Videos Library
 * ```/config``` -> Plex config directory


##Install
To run the latest plex media server version:

``` bash
docker run -d --name="plex" \
  -v /path/to/plex/config:/config \
  -v /path/to/tv/dir:/tv \
  -v /path/to/movies/dir:/movies \
  -v /path/to/music/dir:/music \
  -v /path/to/photos/dir:/photos \
  -v /path/to/videos/dir:/videos \
  -v /etc/localtime:/etc/localtime:ro \
  -p 34200:34200 \
  kierranm/plex
```

If you would like to specify a specific version of plex to run:

``` bash
docker run -d --name="plex" \
  -v /path/to/plex/config:/config \
  -v /path/to/tv/dir:/tv \
  -v /path/to/movies/dir:/movies \
  -v /path/to/music/dir:/music \
  -v /path/to/photos/dir:/photos \
  -v /path/to/videos/dir:/videos \
  -v /etc/localtime:/etc/localtime:ro \
  -e VERSION=0.9.9.8.436-8abe5c0 \
  -p 34200:34200 \
  kierranm/plex
```

NOTE: It can be the partial or full version name (e.g. 0.9.9.8 or 0.9.9.8.436-8abe5c0) replace with the version you desire in the command above
The VERSION variable supports versions listed on <a href="https://plex.tv/downloads/1/archive">here</a>

If you exclude the VERSION tag it'll autoupdate to the latest version whenever you restart the container.

##Post Install
After install go to:

http://server-ip:32400/web/index.html and login with your myPlex credentials
