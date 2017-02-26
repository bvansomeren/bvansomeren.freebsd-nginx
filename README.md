bvansomeren.freebsd-nginx
=========

Simple role to install Nginx to FreeBSD (for example in a jail).  
Does not do much more than setup the defaults right now, check back later for vhost support.

Requirements
------------

Just FreeBSD and packages.

Role Variables
--------------

```
freebsd_nginx_package: nginx
```

Selects the package to be installed; You could also chose _nginx-devel_ to get the cutting edge features.

```
freebsd_nginx_user: nobody
```

Set the user that nginx wil run under

```
freebsd_nginx_worker_processes: "{{ ansible_processor_count }}"
```

Sets the worker processes, documentation says 1 per cpu so that's what we default to.

```
freebsd_nginx_worker_connections: 1024
```

Number of max connections per worker process.

```
freebsd_nginx_sendfile: "on"
```

Should sendfile be on by default

```
freebsd_nginx_gzip: "on"
```

Enable gzip by default

```
freebsd_nginx_default_enabled: yes
```

Determines if you want the default host to be active. The below settings depend on this

```
freebsd_nginx_default_charset: "utf-8"
```

Default to UTF-8 characterset.

```
freebsd_nginx_default_docroot: "/usr/local/www/nginx"
```

The folder that contains the web files. Please note that the default can be overwritten by new installs of Nginx.

```
freebsd_nginx_default_index: "index.html index.htm"
```

Default index files

```
freebsd_nginx_logfolder: /var/log/nginx
```

Where nginx by default should write it's logs

```
freebsd_nginx_includes:
- "vhosts/*.conf"
```

Should you want to place your includes elsewhere, change the above.

```
freebsd_nginx_ssl_generate_dhparam: no
```

A value of no means we copy the premade dhparams.pem to the server. You can also replace the file yourself.
Changing this to yes will generate this file once (which will take a while on slow hardware)

Dependencies
------------

None, some of my roles might depend on this role.

Example Playbook
----------------

Lame example; Better example soon.

    - hosts: servers
      roles:
         - { role: bvansomeren.freebsd-nginx }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
