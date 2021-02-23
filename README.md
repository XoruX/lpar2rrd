# XoruX LPAR2RRD
This is dockerized version of single [XoruX](https://www.xorux.com) application - [LPAR2RRD](https://www.lpar2rrd.com).

It's based on the latest official [Alpine Linux](https://hub.docker.com/_/alpine) with all necessary dependencies installed.

Quick start:

    docker run -d --name LPAR2RRD --restart always -v lpar2rrd-data:/home/lpar2rrd/lpar2rrd/data -v lpar2rrd-etc:/home/lpar2rrd/lpar2rrd/etc -p 8080:80 xorux/lpar2rrd

You can set container timezone via env variable TIMEZONE in docker run command:

    docker run -d --name LPAR2RRD --restart always -v lpar2rrd-data:/home/lpar2rrd/lpar2rrd/data -v lpar2rrd-etc:/home/lpar2rrd/lpar2rrd/etc -p 8080:80 -e TIMEZONE="Europe/Prague" xorux/lpar2rrd

Application UI can be found on http://<CONTAINER_IP>, use admin/admin for login.

You can connect via SSH on port 22 (exposed), username **lpar2rrd**, password **xorux4you** - please change it ASAP.
