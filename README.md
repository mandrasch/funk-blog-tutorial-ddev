This repo is used on https://statamictutorials.com by Jonas Siewertsen

Added DDEV via: 
```
ddev config --project-type=laravel --docroot=public
# browsersync / mix support added via docker-composer.browsersync.yaml,
# HTTPS is currently not supported of the box, in future you can just get
# the official one via ddev get drud/ddev-browsersync
# https://github.com/drud/ddev-browsersync/pull/21
# Added browsersync in webpack.mix.js + footer, see commits
ddev restart
```

## Local setup after cloning

```
ddev start
# Generate config, set APP_URL & generate key
ddev exec "cp .env.example .env"
ddev exec 'sed -i "/APP_URL=/c APP_URL=$DDEV_PRIMARY_URL" .env'
ddev artisan key:generate
# Composer install
ddev composer install

# Add support for CLI please command via simple DDEV-addon:
# (https://github.com/mandrasch/ddev-addon-statamic-please)
ddev get mandrasch/ddev-addon-statamic-please

# Compile JS/SCSS
ddev exec npm install
ddev exec npm run dev
```

Afterwards you only need to run those two commands to develop locally:

```
ddev launch
ddev exec npm run watch
# reload browser to activate browsersync
```

See more: https://my-ddev-lab.mandrasch.eu/tutorials/cms-and-frameworks/statamic.html
