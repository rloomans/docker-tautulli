![http://linuxserver.io](http://www.linuxserver.io/wp-content/uploads/2015/06/linuxserver_medium.png)

## This is a Container in active development, and should not be used by the general public.
If you are currious about the current progress or want to comment\contribute to this work, feel free to join us at out irc channel:
[IRC](http://www.linuxserver.io/index.php/irc/) on freenode at `#linuxserver.io`.

# linuxserver/<container-name>

<Provide a short, concise description of the application. No more than two SHORT paragraphs. Link to sources where possible and include an image illustrating your point if necessary. Point users to the original applications website, as that's the best place to get support - not here.>

## Usage

```
docker create --name=<container-name> -v /etc/localtime:/etc/localtime:ro -v <path to data>:/config -e PGID=<gid> -e PUID=<uid>  -p 1234:1234 linuxserver/<container-name>
```

**Parameters**

* `-p 4242` - the port(s)
* `-v /etc/localhost` for timesync - *optional*
* `-v /config` -
* `-e PGID` for for GroupID - see below for explanation
* `-e PUID` for for UserID - see below for explanation

It is based on phusion-baseimage with ssh removed, for shell access whilst the container is running do `docker exec -it quassel-core /bin/bash`.

### User / Group Identifiers

**TL;DR** - The `PGID` and `PUID` values set the user / group you'd like your container to 'run as' to the host OS. This can be a user you've created or even root (not recommended).

Part of what makes our containers work so well is by allowing you to specify your own `PUID` and `PGID`. This avoids nasty permissions errors with relation to data volumes (`-v` flags). When an application is installed on the host OS it is normally added to the common group called users, Docker apps due to the nature of the technology can't be added to this group. So we added this feature to let you easily choose when running your containers.

## Setting up the application 

<Insert a basic user guide here to get a n00b up and running with the software inside the container.> DELETE ME


## Updates

* Upgrade to the latest version simply `docker restart <container-name>`.
* To monitor the logs of the container in realtime `docker logs -f <container-name>`.


**Credits**

* lonix <lonixx@gmail.com>
* IronicBadger <ironicbadger@linuxserver.io>

**Versions**

* 2.0 
* 1.0