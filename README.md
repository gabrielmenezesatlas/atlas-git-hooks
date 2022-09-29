# Atlas Git Hooks

Package developed to automate and change the main folder referring to git hooks.

## Installation
Add private repository in composer json file:

```json
{
  ...
  "repositories": [
    {
      "type": "vcs",
      "url": "git@github.com:gabrielmenezesatlas/atlas-git-hooks.git"
    }
  ]
}
```

Require this package with composer:
```bash
composer require --dev gabrielmenezesatlas/atlas-git-hooks
```

You can install the package:
```bash
php artisan atlas-git-hooks:git-hooks-install
```

## Usage

Change the pre-commit template file created in .atlasHooks/pre-commit and add the action you want to take before the user successfully commits.

Example if you are using docker:
```bash
#!/bin/sh
. "$(dirname "$0")/_/hooks.sh"

cd ..
docker-compose up --detach --no-deps --no-recreate {container-name}
docker-compose exec -T {container-name} php artisan test
```

You can use other git hooks as per the [documentation](https://git-scm.com/docs/githooks).

## Credits
This package was inspired by the [npm husky package](https://github.com/typicode/husky).

Package created by [Gabriel Menezes](https://github.com/gabrielmenezesatlas).
