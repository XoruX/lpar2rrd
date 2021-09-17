# XoruX LPAR2RRD
This is dockerized version of single [XoruX](https://www.xorux.com) application - [LPAR2RRD](https://www.lpar2rrd.com).

It's based on the latest official [Alpine Linux](https://hub.docker.com/_/alpine) with all necessary dependencies installed.

Quick start:

    docker run -d --name LPAR2RRD --restart always -v lpar2rrd:/home/lpar2rrd xorux/lpar2rrd

You can set container timezone via env variable TIMEZONE in docker run command:

    docker run -d --name LPAR2RRD --restart always -v lpar2rrd:/home/lpar2rrd -e TIMEZONE="Europe/Prague" xorux/lpar2rrd

If you want to use this container as a XorMon backend, set XORMON env variable:

    docker run -d --name LPAR2RRD --restart always -v lpar2rrd:/home/lpar2rrd -e XORMON=1 xorux/lpar2rrd

Application UI can be found on http://\<CONTAINER_IP\>, use admin/admin for login.

