# Enable HTTP Authentication
First, install Apache Utilities:
```bash
sudo apt-get update
sudo apt-get install apache2-utils
```
This will install the htpasswd tool, which we will use to generate the password file.

Then run the `htpasswd` command, inserting the desired username:
```bash
sudo htpasswd -c /etc/nginx/.htpasswd user_name_here
```
You will then be prompted for a password.

To require authentication in your web app, add this to your nginx config:
```bash
auth_basic "Restricted Content";
auth_basic_user_file /etc/nginx/.htpasswd;
```
Then restart nginx:
```bash
sudo systemctl restart nginx
```
Then you should be good to go!