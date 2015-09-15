# tutum-blazing-wordpress

This is a blazing fast WordPress stack for [Tutum](https://www.tutum.co/).

## Known issues

### Permissions

If WordPress asks for FTP credentials or is otherwise unhappy with permissions. run the following command on the Docker host. (Credit: [@md5](https://github.com/docker-library/wordpress/issues/24#issuecomment-63256094))

```sh
docker exec CONTAINER_NAME chown -R www-data:www-data /var/www/html
```

### Availability

This stack provides zero fault tolerance. While haproxy and Varnish can easily be scaled to multiple containers,
MySQL and WordPress files would require replication.
