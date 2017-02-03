# rsyslogd

Side-car container with running system logging demon.

This container can be attached to an arbitrary amount of containers as their log
demon. Useful for catching and collecting logs inside a docker-compose
composition without Docker.

# Make It Short

This container enables system logging. Just type:

~~~~
$ docker run -d \
    --name syslog \
    blacklabelops/rsyslogd
~~~~

> Starts a rsyslog demon.

Now attach a different container and use logger:

~~~~
$ docker run -it \
    --volumes-from syslog \
    blacklabelops/centos \
    bash
$ logger hello world
$ cat /var/log/messages
~~~~

> This will open a console inside another container, you can log and read the messages.

# How it works

The Container exposes the logging socket `/dev/log` as a Docker volume. The statement `--volumes-from syslog` mounts
this volume and logs without having to run a syslog demon locally.

# Support

Leave a message and ask questions on Hipchat: [blacklabelops/hipchat](http://support.blacklabelops.com)

# References

* [Rsyslod Homepage](http://www.rsyslog.com/)
* [Docker Homepage](https://www.docker.com/)
* [Docker Userguide](https://docs.docker.com/userguide/)
