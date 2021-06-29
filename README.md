# Nextcloud App Gitpod
Guide on how to set up a Nextcloud App Repository to be able to open it in gitpod with an automatic dev server.

This repository contains:
- A gitpod config file, that automatically spins up three tasks:
  - A Docker compose server with Nextcloud, Mariadb and Phpmyadmin
  - A terminal wich builds the frontend files (eg. vue -> js bundle with webpack)
  - An empty terminal for use while programming

To set this up for your Nextcloud App only slight modifications are necessary.

## Guide
1. Copy all files in this repository (except README.md) into your repo

2. The Nextcloud and MariaDB containers need passwords to authenticate and initialize properly. But gitpod has acess control to these websites built in (unless you manually set the port 8080 or 8081 to public). So the strength of these passwords is pretty much irrelevant. Also these dev servers have random domains each time they get spun up and contain no sensitive information. This repo contains randomly generated passwords in the gitpod/docker-compose.yml file. You can change them if you like, but as descibed above it doesn't really matter. If your repository is public they are public anyways. If for some reason you want to hide these passwords you can implement a system, that randomly generates them on dev server spin up.

3. Edit the init command of the dependency install task and the command of the Frontend task in the gitpod.yml, to match your apps commands.

defaults (compatible with the [tutorial app by nextcloud](https://github.com/nextcloud/app-tutorial)):
  - Dependency install: make dev-setup
  - Frontend: make watch-js

4. Open https://gitpod.io/#https://github.com/[your_user]/[your_repo]/ or install the [gitpod browser extension](https://www.gitpod.io/docs/browser-extension/).
