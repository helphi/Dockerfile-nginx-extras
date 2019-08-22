# nginx-extras Docker image

## Tags

- `1.14.2`

## Usage

> Tips:
> webdav enabled by default with no auth, refer to `/etc/nginx/conf.d/default.conf`

```bash
mkdir -p /usr/share/nginx/html
chown -R www-data:www-data /usr/share/nginx/html

docker run -d --name=ng \
  -p 80:80 \
  -v /usr/share/nginx/html:/usr/share/nginx/html \
  helphi/nginx-extras:1.14.2

######## test webdav ########

#create dir
curl -X MKCOL 'http://localhost/webdav/'
#upload file
curl -T '/etc/hosts' 'http://localhost/webdav/'
#download file
curl 'http://localhost/webdav/hosts'
#rename file
curl -X MOVE --header 'Destination:http://localhost/webdav/hosts.bak' 'http://localhost/webdav/hosts'
#delete file
curl -X DELETE 'http://localhost/webdav/hosts.bak'
#delete dir
curl -X DELETE 'http://localhost/webdav/'
```
