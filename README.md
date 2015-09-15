# tutum-blazing-wordpress

This is a blazing fast WordPress stack for [Tutum](https://www.tutum.co/).

## Known issues

### Permissions

If WordPress asks for FTP credentials or is otherwise unhappy with permissions. run the following command on the Docker host.

```sh
docker exec CONTAINER_NAME chown -R www-data:www-data /var/www/html
```

### Availability

This stack provides zero fault tolerance. While haproxy and Varnish can easily be scaled to multiple containers,
MySQL and WordPress files would require replication.
