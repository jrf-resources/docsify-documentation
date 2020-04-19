## How to mount a Google Drive Bucket to Ubuntu

### Download Google Cloud SDK, extract, and run install.sh

First, download the Google Cloud SDK archive file:
```bash
mkdir ~/apps
cd ~/apps
wget https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-sdk-156.0.0-linux-x86_64.tar.gz
```
Extract the archive file:
```bash
tar xvzf google-cloud-sdk-156.0.0-linux-x86_64.tar.gz
rm -rf google-cloud-sdk-156.0.0-linux-x86_64.tar.gz
```
Run the install script to add Cloud SDK tools to your path, enable command-completion in your bash shell, and/or and enable usage reporting:
```bash
./google-cloud-sdk/install.sh
```
Afterwards, update your source file:
```bash
source /path/to/.bashrc
```
### Run core gcloud commands to authenticate your SDK to Google Cloud account

To authenticate run:
```bash
gcloud auth login
```
And follow the on screen instructions.

To get default auth key:
```bash
gcloud auth application-default login
```
And follow the on screen instructions.

### Install gcsfuse on Ubuntu

Add the gcsfuse distribution URL as a package source and import its public key:
```bash
export GCSFUSE_REPO=gcsfuse-`lsb_release -c -s`
echo "deb http://packages.cloud.google.com/apt $GCSFUSE_REPO main" | sudo tee etc/apt/sources.list.d/gcsfuse.list
curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
```

Update the list of packages available and install gcsfuse:
```bash
sudo apt-get update
sudo apt-get install gcsfuse
```

### Use gcsfuse to mount Google Drive Bucket
Use the following command to mount a bucket:
```bash
gcsfuse bucket-name /path/to/mount
```

To ummount:
```bash
fusermount -u /path/to/mount
```

***To add: Add gcsfuse mount to startup

## How to install MySQL on Ubuntu 16.04
Install MySQL:
```bash
sudo apt-get update
sudo apt-get install mysql-server
```
Configure MySQL:
```bash
sudo mysql_secure_installation
```
Check status:
```bash
systemctl status mysql
```

## How to install Nginx on Ubuntu 16.04 
Install Nginx:
```bash
sudo apt-get update
sudo apt-get install nginx
```
Adjust the firewall:
```bash
sudo ufw allow "Nginx Full"
```
Check status:
```bash
systemctl status nginx
```

## How to Enable HTTP Authentication
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

## How to install Node.js from a PPA on Ubuntu 16.04

Create a downloads folder, `cd` into it, and use `curl` to retrieve the Node.js installation script:
```bash
mkdir ~/downloads
cd ~/downloads
curl -sL https://deb.nodesource.com/setup_6.x -o nodesource_setup.sh
```
Run the script as sudo:
```bash
sudo bash nodesource_setup.sh
```
Install the Node.js package:
```bash
sudo apt-get install nodejs
```
Install the `build-essential` package to make sure all of Node.js functions properly:
```bash
sudo apt-get install build-essential
```
