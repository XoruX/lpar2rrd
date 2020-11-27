# XoruX LPAR2RRD Docker
This is dockerized version of single [XoruX](https://www.xorux.com) application - [LPAR2RRD](https://www.lpar2rrd.com).

It's based on the latest official [Alpine Linux](https://hub.docker.com/_/alpine) with all necessary dependencies installed.

Quick start:

    docker run -d --name LPAR2RRD --restart always -p 8080:80 xorux/lpar2rrd

or better 

    XORUX_DIR=/srv/xorux   # select any directory with rwx owner permissions
    mkdir -p $XORUX_DIR/lpar2rrd
    chown 1005 $XORUX_DIR/lpar2rrd # 1005 is uid of user lpar2rrd inside the container
    docker run -d --name LPAR2RRD --restart always -v $XORUX_DIR/lpar2rrd:/home/lpar2rrd/lpar2rrd -p 8080:80 xorux/lpar2rrd

If you run container with volume params, it will use XORUX_DIR to store all data and configurations for easy backups, log access and further upgrades.

You can set container timezone via env variable TIMEZONE in docker run command:

    docker run -d --name LPAR2RRD --restart always -v $XORUX_DIR/lpar2rrd:/home/lpar2rrd/lpar2rrd -p 8080:80 -e TIMEZONE="Europe/Prague" xorux/lpar2rrd

Application UI can be found on http://<CONTAINER_IP>, use admin/admin for login.

You can connect via SSH on port 22 (exposed), username **lpar2rrd**, password **xorux4you** - please change it ASAP.
