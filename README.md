# Drupal training
This is a DDEV-based Drupal development environment.

### Software requirements
* [Docker & DDEV-Local](https://ddev.readthedocs.io/en/stable/#installation)

## Setup

### Clone the repo:
```
git clone git@github.com:mariohernandez/drupaltraining.git
```

### Build the project:
Ensure Docker is running before proceeding.

```
cd drupaltraining
```

```
ddev start
```
This will run all the necessary tasks to build your development environment:
* Install theme-required version of node
* Composer install to download Drupal core, modules, drush, and other dependencies
* Import custom database for Drupal
* Update database
* Clear caches
* Launch new site

### Login to Drupal
http://drupaltraining.ddev.site/user/

Username: `admin`, password: `admin`

## Working with the theme
The custom Drupal theme, `training_theme`, can be found in `web/themes/custom/`.  Commands to interact with the theme can be ran from anywhere whithin this project.

### Install theme dependencies
```bash
ddev nvm install && ddev nvm use
```
* This will install version of node declared in `.nvmrc` and will set the theme to use it.

```bash
ddev npm install
```
* This command will install all of the theme's node dependencies (Gulp, Pattern Lab, Autoprefixer, Browsersync, eslint, sass-lint, and others).
* These last two commands above may only be need to run once.

### Build/Compile the theme
```bash
ddev npm run build
```
* This command builds the entire codebase for the theme.
* If you encountered npm errors, run `ddev npm rebuild node-sass`, and try the build command again.

### Clear Drupal caches
To ensure Drupal is able to access all the theme's assets after building the
theme above, clear Drupal's caches.
```bash
ddev drush cr
```

### Run the watch task to access Pattern Lab
```bash
ddev npm run watch
```
* In addition to compiling the theme, this tasks stays running to watch for new code changes within the theme, then automatically compiles them.
* While the watch task is running, you can access Pattern Lab by going to `https://drupaltraining.ddev.site:3000`, or port 3001 if using `http`.

## Interacting with DDev
Official <a target="_blank" href="https://ddev.readthedocs.io/en/stable/">DDEV-Local docs</a>.

```bash
ddev poweroff
```
_Stop DDev if not longer using_.

```bash
ddev start
```
_Start DDev to work on project_.

```bash
ddev delete --omit-snapshot --yes
```
_If project is no longer needed, this will wipe everything out including database.  Use `ddev start` to rebuild project from scratch_.

### Running Drush commands
```bash
ddev drush <command>
```
example: `ddev drush cr`, `ddev drush updb -y`, etc.
