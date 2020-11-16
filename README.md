# XoruX Docker Image
This is Docker image of [XoruX](https://www.xorux.com) applications - [LPAR2RRD](http://www.lpar2rrd.com) & [STOR2RRD](http://www.stor2rrd.com).

It's based on the latest official [Alpine Linux](https://hub.docker.com/_/alpine) with all necessary dependencies installed.

Quick start:

    docker run -d --name XoruX --restart always -p 8080:80 xorux/apps

or better 

    XORUX_DIR=/srv/xorux   # select any directory with rwx owner permissions
    mkdir -p $XORUX_DIR/lpar2rrd $XORUX_DIR/stor2rrd
    chown 1005 $XORUX_DIR/lpar2rrd $XORUX_DIR/stor2rrd   # 1005 is uid of user lpar2rrd inside the container
    docker run -d --name XoruX --restart always -v $XORUX_DIR/lpar2rrd:/home/lpar2rrd/lpar2rrd -v $XORUX_DIR/stor2rrd:/home/stor2rrd/stor2rrd -p 8080:80 xorux/apps

If you run container with volume params, it will use XORUX_DIR to store all data and configurations for easy backups, log access and further upgrades.

You can set container timezone via env variable TIMEZONE in docker run command:

    docker run -d --name XoruX --restart always -v $XORUX_DIR/lpar2rrd:/home/lpar2rrd/lpar2rrd -v $XORUX_DIR/stor2rrd:/home/stor2rrd/stor2rrd -p 8080:80 -e TIMEZONE="Europe/Prague" xorux/apps

or later in web UI.

On first run:

- visit web GUI on port 80 (mapped to host port 8080 in example)
- continue to LPAR2RRD and use admin/admin as username/password
- or continue to STOR2RRD and use admin/admin as username/password

You can connect via SSH on port 22 (exposed), username **lpar2rrd**, password **xorux4you** - please change it ASAP.
