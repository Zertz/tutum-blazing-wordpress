# tutum-blazing-wordpress

This is a blazing fast WordPress stack for [Tutum](https://www.tutum.co/).

**Powered by**

- [tutum/haproxy:0.2](https://hub.docker.com/r/tutum/haproxy/)
- [mysql:5.6](https://hub.docker.com/_/mysql/)
- [benhall/docker-varnish:latest](https://hub.docker.com/r/benhall/docker-varnish/) (more info in [this article](http://blog.benhall.me.uk/2015/01/scaling-wordpress-varnish-docker/))
- [wordpress:4.3-apache](https://hub.docker.com/_/wordpress/)

## Known issues

### Permissions

If WordPress asks for FTP credentials or is otherwise unhappy with permissions, run the following command on the Docker host. (Credit: [@md5](https://github.com/docker-library/wordpress/issues/24#issuecomment-63256094))

```sh
docker exec CONTAINER_NAME chown -R www-data:www-data /var/www/html
```

Alternatively, I published a WordPress image on [Docker Hub](https://hub.docker.com/r/zertz/docker-wordpress-extras/) from `wordpress:4.3-apache` that solves this issue and adds `mbstring` for WPML.

### Availability

This stack provides zero fault tolerance. While haproxy and Varnish can easily be scaled to multiple containers,
MySQL and WordPress files would require replication.
