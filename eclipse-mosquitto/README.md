<!--

********************************************************************************

WARNING:

    DO NOT EDIT "eclipse-mosquitto/README.md"

    IT IS AUTO-GENERATED

    (from the other files in "eclipse-mosquitto/" combined with a set of templates)

********************************************************************************

-->

# Supported tags and respective `Dockerfile` links

-	[`1.6.8`, `1.6`, `latest`](https://github.com/eclipse/mosquitto/blob/6bfd52af9e29165bbf82e3c67b0c4f8310e92b43/docker/1.6/Dockerfile)
-	[`1.5.9`, `1.5`](https://github.com/eclipse/mosquitto/blob/6bfd52af9e29165bbf82e3c67b0c4f8310e92b43/docker/1.5/Dockerfile)

# Quick reference

-	**Where to get help**:  
	[the Docker Community Forums](https://forums.docker.com/), [the Docker Community Slack](https://blog.docker.com/2016/11/introducing-docker-community-directory-docker-community-slack/), or [Stack Overflow](https://stackoverflow.com/search?tab=newest&q=docker)

-	**Where to file issues**:  
	[https://github.com/eclipse/mosquitto/issues](https://github.com/eclipse/mosquitto/issues)

-	**Maintained by**:  
	[the Eclipse Foundation](https://github.com/eclipse/mosquitto)

-	**Supported architectures**: ([more info](https://github.com/docker-library/official-images#architectures-other-than-amd64))  
	[`amd64`](https://hub.docker.com/r/amd64/eclipse-mosquitto/), [`arm32v6`](https://hub.docker.com/r/arm32v6/eclipse-mosquitto/), [`arm64v8`](https://hub.docker.com/r/arm64v8/eclipse-mosquitto/), [`i386`](https://hub.docker.com/r/i386/eclipse-mosquitto/), [`ppc64le`](https://hub.docker.com/r/ppc64le/eclipse-mosquitto/), [`s390x`](https://hub.docker.com/r/s390x/eclipse-mosquitto/)

-	**Published image artifact details**:  
	[repo-info repo's `repos/eclipse-mosquitto/` directory](https://github.com/docker-library/repo-info/blob/master/repos/eclipse-mosquitto) ([history](https://github.com/docker-library/repo-info/commits/master/repos/eclipse-mosquitto))  
	(image metadata, transfer size, etc)

-	**Image updates**:  
	[official-images PRs with label `library/eclipse-mosquitto`](https://github.com/docker-library/official-images/pulls?q=label%3Alibrary%2Feclipse-mosquitto)  
	[official-images repo's `library/eclipse-mosquitto` file](https://github.com/docker-library/official-images/blob/master/library/eclipse-mosquitto) ([history](https://github.com/docker-library/official-images/commits/master/library/eclipse-mosquitto))

-	**Source of this description**:  
	[docs repo's `eclipse-mosquitto/` directory](https://github.com/docker-library/docs/tree/master/eclipse-mosquitto) ([history](https://github.com/docker-library/docs/commits/master/eclipse-mosquitto))

# What is Eclipse Mosquitto?

Eclipse Mosquitto is an open source implementation of a server for versions 5, 3.1.1, and 3.1 of the MQTT protocol. Main homepages: http://mosquitto.org/

![logo](https://raw.githubusercontent.com/docker-library/docs/757578e3a44e5460a8a11d32a81776f8b74231a9/eclipse-mosquitto/logo.png)

# How to use this image

## Directories

Three directories have been created in the image to be used for configuration, persistent storage and logs.

	/mosquitto/config
	/mosquitto/data
	/mosquitto/log

## Configuration

When running the image, the default configuration values are used. To use a custom configuration file, mount a **local** configuration file to `/mosquitto/config/mosquitto.conf`

```console
$ docker run -it -p 1883:1883 -p 9001:9001 -v mosquitto.conf:/mosquitto/config/mosquitto.conf eclipse-mosquitto
```

Configuration can be changed to:

-	persist data to `/mosquitto/data`
-	log to `/mosquitto/log/mosquitto.log`

i.e. add the following to `mosquitto.conf`:

	persistence true
	persistence_location /mosquitto/data/
	log_dest file /mosquitto/log/mosquitto.log

**Note**: If a volume is used, the data will persist between containers.

## Run

Run a container using the new image:

```console
$ docker run -it -p 1883:1883 -p 9001:9001 -v mosquitto.conf:/mosquitto/config/mosquitto.conf -v /mosquitto/data -v /mosquitto/log eclipse-mosquitto
```

**Note**: if the mosquitto configuration (mosquitto.conf) was modified to use non-default ports, the docker run command will need to be updated to expose the ports that have been configured.

# License

Eclipse Mosquitto is released under the [EPL](https://www.eclipse.org/legal/epl-v10.html)/[EDL](https://eclipse.org/org/documents/edl-v10.php)

As with all Docker images, these likely also contain other software which may be under other licenses (such as Bash, etc from the base distribution, along with any direct or indirect dependencies of the primary software being contained).

Some additional license information which was able to be auto-detected might be found in [the `repo-info` repository's `eclipse-mosquitto/` directory](https://github.com/docker-library/repo-info/tree/master/repos/eclipse-mosquitto).

As for any pre-built image usage, it is the image user's responsibility to ensure that any use of this image complies with any relevant licenses for all software contained within.
