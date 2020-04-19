# Linux Desktop Setup
### Software Installs
#### One Line Apt Installs
```bash
sudo apt install tilix
```
#### Sublime Text
```bash
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
sudo apt-get install apt-transport-https
echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
sudo apt-get update
sudo apt-get install sublime-text
```
#### Brave Browser
```bash
sudo apt install apt-transport-https curl
curl -s https://brave-browser-apt-release.s3.brave.com/brave-core.asc | sudo apt-key --keyring /etc/apt/trusted.gpg.d/brave-browser-release.gpg add -
echo "deb [arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main" | sudo tee /etc/apt/sources.list.d/brave-browser-release.list
sudo apt update
sudo apt install brave-browser
```
### Core Snaps To Install
```bash
sudo snap install gitkraken
sudo snap install termius-app
sudo snap install spotify
sudo snap install slack --classic
sudo snap install code --classic
sudo snap install bitwarden
sudo snap install standard-notes
sudo snap install insomnia
```
### Other Snaps
```bash
sudo snap install multipass --classic
sudo snap install postman
sudo snap install notepad-plus-plus
sudo snap install slack-term
sudo snap install snap-store
sudo snap install atom --classic
sudo snap install skype --classic
```
### Install Linuxbrew
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/Linuxbrew/install/master/install.sh)"
```
### Homebrew Post Install Steps (taken from terminal)
- Install the Homebrew dependencies if you have sudo access:
  Debian, Ubuntu, etc.
```
sudo apt-get install build-essential
```
- Configure Homebrew in your ~/.profile by running
```
echo 'eval $(/home/linuxbrew/.linuxbrew/bin/brew shellenv)' >>~/.profile
```
- Add Homebrew to your PATH
```
eval $(/home/linuxbrew/.linuxbrew/bin/brew shellenv)
```
- We recommend that you install GCC by running:
```
brew install gcc
```
- Run `brew help` to get started
- Further documentation: https://docs.brew.sh
### Homebrew Installs
```bash
brew install hugo
```
### Framework Installs
```bash
sudo apt-get install curl
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt install -y nodejs
npm install -g create-react-app nodemon
```
