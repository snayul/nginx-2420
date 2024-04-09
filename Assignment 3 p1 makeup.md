
first mkdir /srv/2420-files 
and populate it with example files

```bash
sudo mkdir /srv/2420-files
sudo touch examp{a...b}
```
next we create /etc/nginx/sites-available and  /etc/nginx/sites-enabled

```bash 
sudo mkdir -p /etc/nginx/sites-available
sudo mkdir -p /etc/nginx/sites-enabled
```
touch nginx-2420 to /sites-available/ and configure the server block like this (from command line):


```bash
cat <<EOF >> /etc/nginx/sites-available/nginx-2420
server {
    listen 80;
    listen [::]:80;
    server_name _;
    root /srv/2420-files;
    location / {
	    autoindex on;
    }
}

```

reload nginx configuration:
```bash
sudo systemctl reload nginx
```


![[Pasted image 20240409121628.png]]