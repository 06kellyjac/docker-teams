[![Docker Stars](https://img.shields.io/docker/stars/06kellyjac/teams.svg?style=flat-square)](https://hub.docker.com/r/06kellyjac/teams/) [![Docker Pulls](https://img.shields.io/docker/pulls/06kellyjac/teams.svg?style=flat-square)](https://hub.docker.com/r/06kellyjac/teams/) [![Docker Build Status](https://img.shields.io/docker/build/06kellyjac/teams.svg?style=flat-square)](https://hub.docker.com/r/06kellyjac/teams/)

# Supported tags and respective `Dockerfile` links

- [`debian`, `buster-slim`, `debian-buster-slim`, `latest`: (*debian-buster-slim/Dockerfile*)](https://gitlab.com/06kellyjac/docker_teams/blob/master/debian-buster-slim/Dockerfile)
  - **XKB Compressed**

The Docker file also visible on the Docker Hub page: <https://hub.docker.com/r/06kellyjac/teams/~/dockerfile/>

# How to use this image

This image is slightly difficult as you will need to mount your X11 Unix Socket.

If you can get docker + xeyes working (or some other docker + GUI container) then this *'should'* work just fine.

```bash
# Minimal:
docker run -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix$DISPLAY 06kellyjac/teams &

# Example command: (See below for details)
docker run -v /tmp/.X11-unix:/tmp/.X11-unix \
-e DISPLAY=unix$DISPLAY \
-v ~/.config/teams-for-linux:/teams-for-linux \
06kellyjac/teams &

# Example command flat:
docker run -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix$DISPLAY -v ~/.config/teams-for-linux:/teams-for-linux 06kellyjac/teams &
```

Add `--rm` remove the container when closed

Use `--name X` to name the container something easier to deal with than the random one.

To save your config, add the following:
`-v /wherever:/teams-for-linux`
Put it in `$XDG_CONFIG_HOME/teams-for-linux` to use your config with native `teams-for-linux`.
`$XDG_CONFIG_HOME` may be empty, the default location is `~/.config`

**IMPORTANT** - You should create your folder before running the container to ensure it has a user id of `1000`.

If you are not user id `1000` then you can either make your config folder for user id `1000` or try play with 'namespaces' and mounting `passwd` and `groups` in read-only if your kernel supports it.

# Quick reference

- **Where to get help**:  
  [I have contact details on my Github](https://gitlab.com/06kellyjac), [the Docker Community Forums](https://forums.docker.com/), [the Docker Community Slack](https://blog.docker.com/2016/11/introducing-docker-community-directory-docker-community-slack/), or [Stack Overflow](https://stackoverflow.com/search?tab=newest&q=docker)

- **Where to file issues**:  
  <https://gitlab.com/06kellyjac/docker_teams/issues>

- **Maintained by**:  
  [06kellyjac on GitLab](https://gitlab.com/06kellyjac)

- **Source of this description**:  
  [The GitLab README.md](https://gitlab.com/06kellyjac/docker_teams/blob/master/README.md) ([history](https://gitlab.com/06kellyjac/docker_teams/commits/master/README.md))

# What is Teams

Teams is a product of Microsoft

This is an Unofficial container of the Unofficial Microsoft Teams client from [ivelkov](https://github.com/ivelkov/)

The goal of this project was to shove Teams into a container.
There is one version shipped:

- `latest` / `debian-buster-slim`
  - Uses .deb release from [teams-for-linux/releases](https://github.com/ivelkov/teams-for-linux/releases)

Thanks go to [ivelkov](https://github.com/ivelkov/) and [contributors](https://github.com/ivelkov/teams-for-linux/graphs/contributors) on GitHub for the Teams Electron wrapper client.

The source used in this image:
[https://github.com/ivelkov/teams-for-linux/](https://github.com/ivelkov/teams-for-linux/)

# Licence

Microsoft Teams is a product of Microsoft and part of their Office 365 workspace. All other trademarks are the property of their respective owners.

View [licence information](https://github.com/ivelkov/teams-for-linux/blob/master/LICENSE.md) for the software contained in this image.

View [licence information](https://mit-license.org/) for the container set-up.
