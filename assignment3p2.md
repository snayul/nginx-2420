First Download the hello-server file to your local machine and go to the command prompt.

```bash
>sftp -i C:\home\cjchanicka\.ssh\do-key Cchanicka@143.110.151.176
> put C:\Users\cjcha\Downloads\hello-server
```
This will add the hello-server file to your users home directory on the virtual machine.

Navigate to /etc/systemd/system
```bash
sudo touch hello-server.service
sudo vim hello-server.service
```
Then use the following as the unit file

![[Pasted image 20240409100554.png]]
sudo system status hello-server to check status
move the hello-server to the /usr/bin/
```bash 
sudo mv hello-server /usr/bin/
```
edit your server block in /etc/nginx/sites-available/nginx-2420

![[Pasted image 20240409110200.png]]
