---
title: "Hugo Deploy"
date: 2019-12-30
draft: false
---
# Hugo Testing and Inital Deployment 
## macOS
### Installation
On macOS, you can install hugo with homebrew:
```sh
brew install hugo
```
To verify your installation:
```sh
hugo version
```
### Site Creation
```sh
hugo new site newsite
cd newsite
```
Download a theme
```sh
git init
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
```
Edit your config.toml configuration file and add the Ananke theme.
```sh
echo 'theme = "ananke"' >> config.toml
```
## Sample header for markdown files
```
---
title: "My First Post"
date: 2019-03-26T08:47:11+01:00
draft: true
---
```