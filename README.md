# lcube.fr
Drupal 8 Proof of concept !

Day 1
-----

Git workflow
http://nvie.com/posts/a-successful-git-branching-model/

```shell
$ git init
$ git add .
$ git commit -m "init codebase"
$ git remote add origin <remote github url>
$ git remote -v
$ git push -u origin master
$ git checkout -b <branch name>
$ git push -u origin <branch name>
```

Drupal console
https://hechoendrupal.gitbooks.io/drupal-console/content/en/index.html

```shell
$ drupal chain --file=install.yml
```

```yaml
commands:
# Download Drupal
  - command: site:new
    arguments:
      directory: 'lcube.dev'
    options:
      latest: 'true'
# Install Drupal
  - command: site:install
    options:
      langcode: 'fr'
      db-type: '%{{db_type|mysql}}'
      db-host: '%{{db_host|127.0.0.1}}'
      db-name: '%{{db_name|lcube.dev}}'
      db-user: '%{{db_user|}}'
      db-pass: '%{{db_pass}}'
      db-port: '%{{db_port|3306}}'
      site-name: 'lcube.dev'
      site-mail: 'info@lcube.fr' # default email
      account-name: 'lcube' # default account
      account-mail: 'info@lcube.fr' # default email
      account-pass: '' # default pass
    arguments:
      profile: 'minimal'
# Start php built-in server
  - command: server
```

Day 2
-----

https://drushcommands.com/

```shell
$ drush make lcube.dev.make --no-core
```

```yaml
core = 8.x
api = 2
defaults[projects][subdir] = contrib

projects[config_update][type] = module
projects[config_update][download][type] = git
projects[config_update][download][url] = https://git.drupal.org/project/config_update.git
projects[config_update][download][tag] = 8.x-1.1

projects[ctools][type] = module
projects[ctools][download][type] = git
projects[ctools][download][url] = https://git.drupal.org/project/ctools
projects[ctools][download][tag] = 8.x-3.0-alpha27

...
```