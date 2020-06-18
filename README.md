# Drupal training (work in progress)

This repo will eventually replace [drupal_training_ddev](https://github.com/mariohernandez/drupal_training_ddev) repo.

## Setup

### Clone the repo:
```
git clone git@github.com:mariohernandez/drupal_training.git
```

### Start the project:
```
cd drupal_training
```

```
ddev start
```
This will run all the necessary tasks in DDev's web container:
* Install theme-required version of node
* Composer install to grab Drupal and all the required modules
* Install Drupal
* Import custom database
* Update database
* Clear caches
* Launch new site

### Login to Drupal
http://training.ddev.site/user/

Username: `admin`, password: `admin`

## Working with the theme
Although the commands to interact with the `training_theme` theme can be ran from anywhere within the project, it's preferably to use `web/themes/custom/training_theme` to avoid confusion.

### Install theme dependencies
```
ddev nvm use
```
```
ddev npm install
```
_These two commands above may only be needed once_.

### Build/compile the theme
```
ddev npm run build
```
If you encountered npm errors, run `ddev npm rebuild node-sass`, and try the build command again.
```
ddev npm run watch
```

## Interacting with DDev
```
ddev poweroff
```
_Stop DDev if not longer using_.

```
ddev start
```
_Start DDev to work on project_.

```
ddev delete --omit-snapshot --yes
```
_If project is no longer needed, this will wipe everything out including database.  Use `ddev start` to rebuild project from scratch_.

### Running Drush commands
```
ddev . drush <your-command>
```
example: `ddev . drush cr`, `ddev . drush uli`, etc.
