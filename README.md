tsar-mod_nginx
==============

#nginx/tengine module for tsar

Support read data from nginx by common socket or unix domain socket.


Quick start
-----------
1. Install [tsar](http://code.taobao.org/p/tsar/src/).
2. Generate a new module by using [tsardevel](http://code.taobao.org/p/tsar/wiki/mod/).

    >`tsardevel ngx_mod`
3. Replace ngx_mod.c.

    >`make`

    >`make install`
4. >`tsar --nginx`

Configuration
-------------
1. Default host is 127.0.0.1 and default port is 80. But we can change both (or one of) the host and port:

    ####example: 
    >`export NGX_TSAR_HOST=192.168.0.1`

    >`export NGX_TSAR_PORT=8080`

2. Stub Status module must be included,and add configuration as below:

    >location =  /nginx_status {
    >
    >         stub_status on;
    >
    >}

3. We can also using unix domain socket, if we set NGX_TSAR_HOST to a filesystem path:

    ####example: 
    >`export NGX_TSAR_HOST=/tmp/nginx-tsar.sock`

    nginx server(which includes the location /nginx_status) must also listen to the unix domain socket path
    >`listen unix:/tmp/nginx-tsar.sock;`

4. The uri and server name send to the nginx server can alse be changed:

    ####example: 
    >`export NGX_TSAR_SERVER_NAME=status.taobao.com`

    >`export NGX_TSAR_URI=/nginx_status`


