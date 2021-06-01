# General pipeline
## Git flow

The overall flow of Gitflow is:

1.  A `develop` branch is created from `master`
2.  A `release` branch is created from `develop`
3.  `Feature` branches are created from `develop`
4.  When a `feature` is complete it is merged into the `develop` branch
5.  When the `release` branch is done it is merged into `develop` and `master`
6.  If an issue in `master` is detected a `hotfix` branch is created from `master`
7.  Once the `hotfix` is complete it is merged to both `develop` and `master`

When starting to work, create a feature branch :

```
git flow feature start FEATURE_NAME
```

When the work is done, you'll want to create a PR into develop
```
git flow feature publish FEATURE_NAME
```


## Setup project

```bash
composer require friendsofphp/php-cs-fixer --dev
composer require league/flysystem-aws-s3-v3 "~1.0"
composer require sammyjo20/lasso
composer require --dev nunomaduro/larastan

php artisan vendor:publish --tag=lasso-config
```

Configure lasso (config file, filesystem, env) locally and on the server. Don't forget to change the `upload_to` key in the lasso config!

Delete assets and add them in gitignore

```	
/public/app/  
/public/backend/  
/public/fonts/vendor  
/public/images/vendor  
/public/mix-manifest.json  
/.php\_cs.cache  
/.lasso
```

put larastan config file in root folder

Add workflow files and secrets in Github

disable quick deploy in ploi
