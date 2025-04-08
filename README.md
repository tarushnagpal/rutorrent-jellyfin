# Docker with rutorrent and jellyfin

A really simple docker compose that sets up containers running [rutorrent](https://github.com/Novik/ruTorrent) & [jellyfin](https://jellyfin.org/) with access to the same directory for shared downloads.

## Setup

You will need to obtain the license key for geoip and replace it in the `geoip-updater.sample.env`, this powers the geoip plugin in rutorrent, you could disable the plugin(and raise a PR to make it optional :D) after putting it in be sure to rename the file

```sh
mv geoip-updater.sample.env geoip-updater.env
```

Post that running a simple,

```sh
docker compose up
```

Should have you up and running! Be sure to add the `-d` for the containers to just run in the background

## How it works

The rutorrent UI should be hosted now on
`localhost:8080` and the jellyfin server on `localhost:8096`, They will share a volume called `/downloads` in the same folder, on jellyfin's UI you would want to setup the media folder on `/media/completed` (Since downloads is mounted to media)

## References
docker rtorrent-rutorrent setup from https://github.com/crazy-max/docker-rtorrent-rutorrent
